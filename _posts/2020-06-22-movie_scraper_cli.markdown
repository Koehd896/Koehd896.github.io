---
layout: post
title:      "Movie Scraper CLI"
date:       2020-06-22 23:35:02 -0400
permalink:  movie_scraper_cli
---


I started the CLI data gem portfolio with a simple goal: create a CLI app that can scrape IMDB for a list of movies and display these movies to the user, allowing them to choose a movie and see more details. Once I was able to successfully scrape the IMDB site, I decided to add some more functionality to my program.

I used nokogiri for scraping which was pretty straightforward, especially since IMDB is a very scrapable site. I was using [this](https://www.imdb.com/chart/moviemeter/?ref_=nv_mv_mpm) list of most popular movies, which lists movies in a table. Each movie is in a new table row element, so it was easy find the css selectors for the movie title and url of the details page. My plan was to scrape this list, create a new movie object (an instance of the Movie class) for each movie on the list. Then I could scrape each movie's detail page for more information like actors and genres. Here's what it looks like using nokogiri:
```  
def self.get_movies(url)
    movies = []
    doc = Nokogiri::HTML(open(url))
    doc.css(".lister-list tr").each do |profile|
      movie = {
        name: profile.css(".titleColumn a").text,
        profile_url: profile.css(".titleColumn a").attribute("href").value
      }
      movies << movie
    end
    movies
  end

  def self.get_attributes(movie_profile_url)
    doc = Nokogiri::HTML(open(movie_profile_url))
    if doc && doc.css(".credit_summary_item")[2]
      actors = doc.css(".credit_summary_item")[2].css("a")[0..2].map do |actor|
        actor.text
      end
      genres = doc.css('.subtext a')[0...-1].map do |genre|
        genre.text
      end
      attritbutes = {
        actors: actors,
        genres: genres
      }
    else
      nil
    end
  end
	```
	
I had to add some conditional statements to the get_attributes class method halfway through writing my program because I was suddenly getting a no method error. I knew this was likely because something had changed on the IMDB website and one or more of the movie detail pages had different css selectors than before. This would explain why nokogiri wasn't returning the correct information and hence why I couln't call the css method on 'nil'. Using pry, I confirmed that there was no issue scraping the list page and creating the movie objects. Rather than having to search through each movie profile page, I decided to add an if statement so that the genre and actor attributes would only be added if they could be successfully scraped. If not, the movie object would be deleted from the @@all collection in the Movie class so that it wouldn't throw any exceptions down the line.

At this point, I had a collection of movie objects with actors and genres attributes. Before going much further, I needed to decide how to structure the code in my CLI class. I knew that I would need many different prompts and error messages, as well as many different instance methods to be called under different conditions. I ultimately framed everything within a loop of displaying output, getting user input, and determining new output based on the user input. I stored error messages and prompts in class constants to declutter the code in other methods. I also created instance variables for the current output, user input, current movie and current list the user is choosing from. This allowed the get_new_output method to essentially reset all of these variables based on various conditions for the next pass of the input loop.

After establising this basic pattern, it was fairly simple to display movies and their details and have the user choose a movie to "play." However, I wanted the user to be able to get a recommendation based on movies their viewing history and the viewing history of other users. This meant I needed to create other users upon starting the program and give all users the ability to rate a movie. I used a 5 "star" rating system (allowing for half stars) and used the following code to instantiate artificial users and have them rate movies:

```
  def make_users
    n = 1
    50.times do
      User.new("user#{n}")
      n += 1
    end
  end

  def make_ratings 
    Movie.all.each do |movie|
      5.times do
        user = User.all.sample
        rating = [1.0, 1.5, 2.0, 2.5, 3.0, 3.5, 4.0, 4.5, 5.0].sample
        View.new(movie, user, rating)
      end
    end
  end
```

This also meant I needed to create a View class so that I could keep track of what each user rated the movies they watched. This established a "has many through" realationship between objects, where users "have many" movies (or had watched many movies) through a viewing (an instance of the View class). Now the user can get a movie recommendation based on actors, genres, their favorite movie, or other users with a similar viewing history. The recommendations based on actors and genres were both based on the users highest rated movie. The actor_rec and genre_rec methods both iterate through all movie objects to find a movie with the same actor or genre as the user's favorite movie that the user hasn't watched yet. For example:
```
  def actor_rec
    recs = self.favorite_movie.actors.map do |actor|
      actor.movies.select {|movie| !self.watched.include?(movie) }
    end
    recs[0][0]
  end
```

To get a recommendation based on other users, the user_rec method iterates through all artificial users to find one that has watched the current user's favorite (highest rated) movie. Then it iterates through that users views to find a movie that the user hasn't watched yet:

```
  def user_rec
    rec_user = User.all.find {|user| user.watched.include?(self.favorite_movie) }
    rec_user.watched.find {|movie| !self.watched.include?(movie) }
  end
```

Creating this CLI app was definitely a learning process but I ended up with a useful program that has some fun, interactive functionality. Feel free to check out the repository on github below, feedback is welcome!

[CLI Movie Scraper](https://github.com/Koehd896/cli-gem)

Happy coding 😊




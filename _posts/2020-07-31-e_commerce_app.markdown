---
layout: post
title:      "E Commerce App"
date:       2020-07-31 06:32:14 -0400
permalink:  e_commerce_app
---


For my sinatra app, I decided to implement a bare bones e commerce site where a user can view items for sale. After signing up or logging in, the user can list items for sale and add items to their cart. The first step was to plan what models I needed and what the relationships would be between those models. The following diagram illustrates the models and their relationships:

[Model Relationship Diagram](https://viewer.diagrams.net/?highlight=0000ff&edit=_blank&layers=1&nav=1&title=e_commerce_app_rel_diagram%20(1).drawio#R7Vxdc6o4GP41XtrhQ9ReHm2756I902337J6zN50UImaLhAmx1f76TQgRIaDUIsbqTKdDXkJI8jzvk4830rHHs8UfBETTO%2BzBoGMZ3qJjX3Usa9gfsv%2FcsBSGnn0pDD5BnjCZmeERvcPUaKTWOfJgnMtIMQ4oivJGF4chdGnOBgjBb%2FlsExzk3xoBHyqGRxcEqvUf5NFp2izHyOzfIfKn8s2mkd6ZAZk5NcRT4OG3nAku6A0OaVrFe0hmIIQhZXfuAHmBpONcTynlLf3WsW7Y34TnvvAx9gMIIhRfuHjGzG7MstxMwAwFvJvXChqlBbHX2dcde0wwpuJqthjDgEMlYRB1uqm4u%2BoHwsut8cDPxyhE%2Ffn07j8DxcPuu%2FPUI920lFcQzNP%2BHQPCqtnvWDZD3B6tXT7DAId%2B%2FEQxe4L1wDzm7VjdnoL4ibVyKW5GBHtzl%2FWk6Gq6lPixXo%2F4JQXP3DSKKXthSrMhL4cRhwIUsrLtKzNJBwGIYpRkF5YpCrxbsMRzKguSqdEELaD3IFjG8zLC3bLCeJIXzvF6TCvDb4MA%2BSG7DuCEP01gzGpyC2Ka3k%2Fyi8qZTtIdSXdBQuGiEgdzhS5zQohnkBLeK%2BkDPUlV6YBp8i1jsyWzTNeZLI0gpae%2FKjpDnV2kwH%2BABJZCgkrUWDMpAsED82wQ%2BgmAeXx4J3sER38B4kOaGiKMQgrJ9SsUvpUggYJgjAPMYQ5xCGW2pHHOiP2x5o6NC6fjsAqMWdrM0uyPZyd0jMOYEkYX%2FirIcHuDHLsRxVH6HoFscknSzkzIjCllripQroVqtf%2BoUKfQDmtCa%2B8LWVtBlmX%2FALaY9ckkSERyijwPhsI%2FubCDDO8SKEv7f9XnRTCKXrk7HlY5HmsAmFabAPRUAJgn%2BGIA0AyFghbGEXBR6N%2BKJ%2FsFmGqL4UdgWhQgWofNbhM255QV0dijIprmoSWxr0DL5zFPWuri7ig4mung4CvpYOOwHEL3xt3X5e2LQcPvb%2Fbf9O7Ovx88dy11wvAzP8svTPh5%2FybzfTe%2FbDihxYAy8y%2BhRiXkhbVAbXm0BnujgDplOaGxzyyFdbOvbAf7AMuB8iqr8xotx73y9cB2RHq1EWljICyvozr%2FOOKRsHxF0CRQ%2BgyN6hTmhHTR2KcutrooKK%2FzUAE3BDOooUvWBWFQG4TDSeGl0umMpUxgNOz2mmuCJnE5hPJdPU2e36%2B8xc8uunu2J%2FafP3782%2B2ZZ6FrSOjq7vXvD0t1r59vfxyN2G0kqCZiV15HdWX9lcTus7hoI3ZnrWtK6waH1jpV6uAMoEBDh6vpT0cgcyeockcocr3BWeWaUTnLOLTK9dSlawTi%2BA0THXf26s4c9Fq%2Bltfxay9fP4uLPmLXO4tdQ2JnH1zs1AAGDzzqHL3f7lN6RS3K6%2FilohbNA6PNwSVZgTWg7kXwfaczvcXbIspfgfgxB%2FEbPdFbO9DbSBS%2FnAfqwe4TGgU%2FeYbU2DgKHvxQr4TyOKP4OyFywPGwvEIlB6uPdzxs8Fyv9uPjSZ9uMvapi4c%2F2ltyvEnrwNZOIPR0k0J1aXDs2yBN4qKP8p3mnu8%2BhK7NKH55BUv2fAlyv5jSDXRTOnXD14MumgEdQ4r7lLoKYLSROlnwWeo%2BLXVtBvHLsVQ3MjwYuwRFFOFQQ8fbHQu7AouDCZ6tbjSc4tSuChd99M4%2B610zetdqOL8cS3WD4iv%2BPlVQVietK%2Flp1PHu6DUPjD5i1z%2BLXUNi12Y4vxxL9TdVuofzd%2FKpvm5ip%2B4fnKbYVQCjjdiV%2FFxDQQh6PpTRG9ZcRJcPMAB8dXSd3cmFvVmTR1M6CzoiLgdD7xv%2FMBtLXj8kP9rnMXyCX1YfWLOSXKxBv1iia1wY5sryW1hMmb5apLCJ1HI9dQ8JYv2SnAPIPIrXvxI2%2BYU5KdiVUldjs8goQW5lJEmfveZrUoZn%2Bo57PhxkVLFlOVJbLwuUiPGcuDB9KmOFUlCvUJBd%2FOqX6AqloIReq4Z%2FgnHqdr7KuIwwbgDiGLl5QqnkKR66gAtEf0n6sWvOIj56ilTGIZ5Yfpgtoq%2BFacOv8DaypWwcdJrhShFiRT5qc0We%2FS3u1mzhCgMPLNeypVObanIPihV2NtarmF%2FWK6OqqEGzxFXHtH0QV6qgyUSwvy6CTAMHu4igdIVEVvs5f7CtwUaP4IndNXXdSzZ9G3JdezccJD1%2Bbyp%2Bi2W4J28a5t8zvNzsTIXsptNvwZnUUMcmZ1pNG3bzpVT5V560zY1Sj8kGjN9rQ0mFq4TeDeJ90IKTfGgtdhgnWU1XPuskVsvTE%2Fm6llTeuLBy1Nw6zV1R01rnprGRmw2yUS5YttJx%2B4G6NtloNsXGfstsrHHKtrnJstHZ92R5163aPXLFsawLJw%2Fyrksrs1%2BgXbGghgb44nt6l7np8kdHbJbMPhIusmcfdrev%2Fwc%3D)

![Model Relationship Diagram](https://viewer.diagrams.net/?highlight=0000ff&edit=_blank&layers=1&nav=1&title=e_commerce_app_rel_diagram%20(1).drawio#R7Vxdc6o4GP41XtrhQ9ReHm2756I902337J6zN50UImaLhAmx1f76TQgRIaDUIsbqTKdDXkJI8jzvk4830rHHs8UfBETTO%2BzBoGMZ3qJjX3Usa9gfsv%2FcsBSGnn0pDD5BnjCZmeERvcPUaKTWOfJgnMtIMQ4oivJGF4chdGnOBgjBb%2FlsExzk3xoBHyqGRxcEqvUf5NFp2izHyOzfIfKn8s2mkd6ZAZk5NcRT4OG3nAku6A0OaVrFe0hmIIQhZXfuAHmBpONcTynlLf3WsW7Y34TnvvAx9gMIIhRfuHjGzG7MstxMwAwFvJvXChqlBbHX2dcde0wwpuJqthjDgEMlYRB1uqm4u%2BoHwsut8cDPxyhE%2Ffn07j8DxcPuu%2FPUI920lFcQzNP%2BHQPCqtnvWDZD3B6tXT7DAId%2B%2FEQxe4L1wDzm7VjdnoL4ibVyKW5GBHtzl%2FWk6Gq6lPixXo%2F4JQXP3DSKKXthSrMhL4cRhwIUsrLtKzNJBwGIYpRkF5YpCrxbsMRzKguSqdEELaD3IFjG8zLC3bLCeJIXzvF6TCvDb4MA%2BSG7DuCEP01gzGpyC2Ka3k%2Fyi8qZTtIdSXdBQuGiEgdzhS5zQohnkBLeK%2BkDPUlV6YBp8i1jsyWzTNeZLI0gpae%2FKjpDnV2kwH%2BABJZCgkrUWDMpAsED82wQ%2BgmAeXx4J3sER38B4kOaGiKMQgrJ9SsUvpUggYJgjAPMYQ5xCGW2pHHOiP2x5o6NC6fjsAqMWdrM0uyPZyd0jMOYEkYX%2FirIcHuDHLsRxVH6HoFscknSzkzIjCllripQroVqtf%2BoUKfQDmtCa%2B8LWVtBlmX%2FALaY9ckkSERyijwPhsI%2FubCDDO8SKEv7f9XnRTCKXrk7HlY5HmsAmFabAPRUAJgn%2BGIA0AyFghbGEXBR6N%2BKJ%2FsFmGqL4UdgWhQgWofNbhM255QV0dijIprmoSWxr0DL5zFPWuri7ig4mung4CvpYOOwHEL3xt3X5e2LQcPvb%2Fbf9O7Ovx88dy11wvAzP8svTPh5%2FybzfTe%2FbDihxYAy8y%2BhRiXkhbVAbXm0BnujgDplOaGxzyyFdbOvbAf7AMuB8iqr8xotx73y9cB2RHq1EWljICyvozr%2FOOKRsHxF0CRQ%2BgyN6hTmhHTR2KcutrooKK%2FzUAE3BDOooUvWBWFQG4TDSeGl0umMpUxgNOz2mmuCJnE5hPJdPU2e36%2B8xc8uunu2J%2FafP3782%2B2ZZ6FrSOjq7vXvD0t1r59vfxyN2G0kqCZiV15HdWX9lcTus7hoI3ZnrWtK6waH1jpV6uAMoEBDh6vpT0cgcyeockcocr3BWeWaUTnLOLTK9dSlawTi%2BA0THXf26s4c9Fq%2Bltfxay9fP4uLPmLXO4tdQ2JnH1zs1AAGDzzqHL3f7lN6RS3K6%2FilohbNA6PNwSVZgTWg7kXwfaczvcXbIspfgfgxB%2FEbPdFbO9DbSBS%2FnAfqwe4TGgU%2FeYbU2DgKHvxQr4TyOKP4OyFywPGwvEIlB6uPdzxs8Fyv9uPjSZ9uMvapi4c%2F2ltyvEnrwNZOIPR0k0J1aXDs2yBN4qKP8p3mnu8%2BhK7NKH55BUv2fAlyv5jSDXRTOnXD14MumgEdQ4r7lLoKYLSROlnwWeo%2BLXVtBvHLsVQ3MjwYuwRFFOFQQ8fbHQu7AouDCZ6tbjSc4tSuChd99M4%2B610zetdqOL8cS3WD4iv%2BPlVQVietK%2Flp1PHu6DUPjD5i1z%2BLXUNi12Y4vxxL9TdVuofzd%2FKpvm5ip%2B4fnKbYVQCjjdiV%2FFxDQQh6PpTRG9ZcRJcPMAB8dXSd3cmFvVmTR1M6CzoiLgdD7xv%2FMBtLXj8kP9rnMXyCX1YfWLOSXKxBv1iia1wY5sryW1hMmb5apLCJ1HI9dQ8JYv2SnAPIPIrXvxI2%2BYU5KdiVUldjs8goQW5lJEmfveZrUoZn%2Bo57PhxkVLFlOVJbLwuUiPGcuDB9KmOFUlCvUJBd%2FOqX6AqloIReq4Z%2FgnHqdr7KuIwwbgDiGLl5QqnkKR66gAtEf0n6sWvOIj56ilTGIZ5Yfpgtoq%2BFacOv8DaypWwcdJrhShFiRT5qc0We%2FS3u1mzhCgMPLNeypVObanIPihV2NtarmF%2FWK6OqqEGzxFXHtH0QV6qgyUSwvy6CTAMHu4igdIVEVvs5f7CtwUaP4IndNXXdSzZ9G3JdezccJD1%2Bbyp%2Bi2W4J28a5t8zvNzsTIXsptNvwZnUUMcmZ1pNG3bzpVT5V560zY1Sj8kGjN9rQ0mFq4TeDeJ90IKTfGgtdhgnWU1XPuskVsvTE%2Fm6llTeuLBy1Nw6zV1R01rnprGRmw2yUS5YttJx%2B4G6NtloNsXGfstsrHHKtrnJstHZ92R5163aPXLFsawLJw%2Fyrksrs1%2BgXbGghgb44nt6l7np8kdHbJbMPhIusmcfdrev%2Fwc%3D)

Note that because I used bcrypt to encrypt the user's password, the actual name of the passowrd column in the Users table was password_digest. Also the User has a direct relationship with the products they create (i.e. list for sale) but not with the products in their cart.

The next step was to plan out the CRUD actions that I wanted the user to be able to perform on their products. I knew I wanted a user to be able to create a product, view that product and modify it's attributes, as well as delete it. However, before implementing this functionality, I needed to ensure that a user could only perform these actions on their own products. For this reason, I started with the sign up and login actions.

After the user fills out the form to sign up, the post route in the users controller and creates a new user object:

```
  post '/signup' do
    filled_in = !params.values[1..-1].include?("")
    confirmed_password = params[:user][:password] == params[:confirm_password]
    unique_usernmae_email = !User.all.find do |user| 
      user.username ==  params[:user][:username] || user.email == params[:user][:email]
    end

    if filled_in && confirmed_password && unique_usernmae_email
      new_user = User.create(params[:user])
      Cart.create(user_id: new_user.id)
      session[:user_id] = new_user.id
      redirect to '/'
    else
      redirect to '/signup'
    end
  end
	```
	
As you can see, a new cart object is also created at this point and associated with the new user. If the user doesn't fill out a required field, uses a username or email already taken, or doesn't accurately re-enter the password, it will redirect to the signup page where the user is prompted to try again.

After signing up, or subsequently logging in, the user is redirected to the index page, but now there are some additional actions they can take. Now a user can create a new product, modify or delete that product through their profile page. These features are made available with some conditional erb statements:

```
<% if logged_in? %>
  <a href="/users/<%= current_user.id %>/cart" %>View Cart</a>
  <form method="post" action="/logout">
    <input type="submit" value="Log Out">
  </form>
  <a href="/users/<%= current_user.id %>">My Profile</a>
<% else %>
  <a href="/signup">Sign Up</a>
  <a href="/login">Log In</a>
<% end %>
```

When a user creates an item they will be redirected to their profile page, where they can view, edit and delete any item they have listed for sale:

```
<% @user.products.each do |product| %>
  <div>
    <p id="product-name"><%= product.name %></p>
    <p id="product-price">Price: $<%= product.price %></p>
    <p id="product-description">Description:<br><%= product.description %></p>
    <p><a href="/products/<%= product.id %>/edit">Edit Product</a></p>
    <p>
      <form method="post" action="/products/<%= product.id %>">
        <input type="hidden" id="hidden" name="_method" value="DELETE">
        <input type="submit" value="Delete Item">
      </form>
    </p>
  </div>
<% end %>
```

A user can also add an item to their cart, in which case the cart_id of that product is set to the user's cart_id. When viewing all the items in their cart, a user can remove an item from the cart.

To take a futher look at the code, check out the [github repo](https://github.com/Koehd896/e_commerce_app) and feel free to reach out with feedback or comments!


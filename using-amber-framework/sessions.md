# Sessions

Session object works just as in Rails.

```crystal
session[:name] = “Merlin”
puts session[:name] # this will work on any page once it has been set as expected.
```

# Flash

Flash object works like in Rails. If you're unfamiliar, it is cleared after it is read.

```crystal
flash[:error] = "Not enough brains."
puts flash[:error] # will display the message and clear on reload
```

Make sure the Flash, Session and CSRF pipelines are enabled in your `routes.cr` file and in the order that the scaffolding puts them.

# CSRF

To use CSRF, enable the pipe in your `routes.cr`

Then, insert the `csrf_tag` helper in your forms.

## How to use CSRF with Ajax

Simply call the `csrf_tag` helper inside your controller and return it as part of a JSON object:

```crystal
def my_action
    {csrf: csrf_tag}.to_json
end
```

In your Javascript, after getting the JSON object back, refresh your CSRF tag with the one from the server.

```javascript
"input[name*=_csrf]").replaceWith(e['csrf']);
```



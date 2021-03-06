#Plockémon
"Gotta link 'em all!"

##Purpose

Work with engineers from another discipline to build a polished application for sharing links

```

        --As a user, I want to be able to:--

        *save links that seem interesting

        *see links that I've saved in the past

        *recommend links to other users

        *see links that other users have recommended to me and who recommended them

        *Moreover, I'd like for any recommendations that get made to be published to
        the #plock_recommendations channel in our Slack team (with the username of both
        the recommender and recommendee)

```


#Api

## To add link to users list
####post "https://plockemon.herokuapp.com/links"

**request**

```
  header: Authorization: "username"
```

body:

```

          {url => "www....",
          title => "Funny Cat",
          description => "Cat cant jump from counter."} in json format
```

**response**

200 - OK

400 - Bad Request

401 - Unauthorized (no username)

403 - Forbidden (username isn't in database)

404 - Not Found

500 - Server Issues

## To get users links
####get "https://plockemon.herokuapp.com/links"

**request**

```
  header: Authorization: "username"
```

**response**

body:

```

         {username => "username",
          links => [
              {url => "www.... ",
              title => "Funny Cat",
              description => "Cat cant jump from counter."},
              {url => "www....",
              title => "Stupid Dog",
              description => "Dog runs away from kitten."}
                    ]
              } in json format
```

400 - Bad Request

401 - Unauthorized (no username)

403 - Forbidden (username isn't in database)

404 - Not Found

500 - Server Issues

## To post recommendations for other users
####post "https://plockemon.herokuapp.com/links/recommended"

**request**

```
header: Authorization: "username"
```

body:

```

          {url => "www....",
          title => "Funny Cat",
          description => "Cat cant jump from counter.",
          recommended_for => "scrappydoo"}
          in json format
```

**response**

400 - Bad Request

401 - Unauthorized (no username)

403 - Forbidden (username isn't in database)

404 - Not Found

500 - Server Issues

## To get users recommendations
####get "https://plockemon.herokuapp.com/links/recommended"

**request**

```
  header: Authorization: "username"
```

**response**

body:

```


          {username => "username",

          links => [

              {url => "www.... ",
              title => "Funny Cat",
              description => "Cat cant jump from counter.",
              recommended_by => "jamesdabbs"},

              {url => "www....",
              title => "Stupid Dog",
              description => "Dog runs away from kitten.",
              recommended_by => "cthulhu"}
                    ]
              } in json format
```

400 - Bad Request

401 - Unauthorized (no username)

403 - Forbidden (username isn't in database)

404 - Not Found

500 - Server Issues

## To delete a link
####delete "https://plockemon.herokuapp.com/links/delete"

**request**

```
header: Authorization: "username"
```

body:

```    
          {title => "Funny Cat"}
          in json format
```

**response**

200 - OK

400 - Bad Request

401 - Unauthorized (no username)

403 - Forbidden (username isn't in database)

404 - Not Found (user has no links)

500 - Server Issues




```


               _,     _,
              /)|    /)\
              \_'-"`/(_/```",,
                /   <        ``--._
                |. _ )     `    *  ',
                ^  ^/_,     *     (\*\
                (#_/  `\)  /'  * - ))_|
                        \  \*   _,//_ *
          Aardwolf       ) >\_* ((|\_/
            Studios      \ | \  | # (
                          \#  \#\ \ #
                           \\  \(  )/
                           _)> _))/(_
           b'ger .-\\,, , /\\//\//\\/),, ,,)/
                   ,\.        .-    -'-,)\/.'))



```

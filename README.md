<link rel="stylesheet" href="https://use.fontawesome.com/releases/v5.1.1/css/all.css"/>

# Elm-Font-Awesome

This package has a really easy-to-use API, with plenty of options!

It comes with a stylesheet and icons helpers:
<div>
  <i class="fas fa-wrench"></i>
  <i class="fab fa-internet-explorer"></i>
  <i class="fas fa-briefcase"></i>
</div>
```elm
import FontAwesome
  exposing ( stylesheet
           , wrench
           , internetExplorer
           , briefcase
           )

view : model -> Html msg
view _
    = div []
    [ stylesheet
    , wrench
    , internetExplorer
    , briefcase
    ]
```


## Customization

This package also has tools for making custom icons:
```elm
import FontAwesome
  exposing ( stylesheet
           , i
           , Icon(Wrench,InternetExplorer,Briefcase)
           )

view : model -> Html msg
view _
    = div []
    [ stylesheet
    , i [] Wrench
    , i [] InternetExplorer
    , i [] Briefcase
    ]
```


### Styling

Some styling shortcuts are included:
```elm
import FontAwesome exposing (..)

view : model -> Html msg
view _
    = div []
    [ stylesheet
    , i [ bordered
        , fixedWidth
        , inverted
        , pullRight
        , spin
        , size Size.Large
        ]
      <| Cog Solid
    ]
```

Don't forget transformations!
```elm
import FontAwesome as FA
  exposing ( i
           , transform
           , Scale(..)
           , ShiftX(..)
           , ShiftY(..)
           , Icon(Magic)
           , Weight(Solid)
           )

view : model -> Html msg
view _
    = div []
    [ stylesheet
    , i [ transform
          { scale  = Just <| Grow 17.1
          , shiftX = Just <| Left 25.5
          , shiftY = Just <| Down 12.9
          , rotate = Just <|      90.0
          }
        ]
      <| Magic Solid
    ]
```


The styling helpers are also included as a record:
```elm
import FontAwesome
  exposing ( i
           , stylesheet
           , style
           ,   Size(..)
           ,   ShiftX(..)
           ,   Animation(..)
           ,   Icon(..)
           ,   Weight(..)
           , Fish
           )

view : model -> Html msg
view _
    = div []
    [ stylesheet
    , i [ style 
          { size       = Just X10
          , fixedWidth = True
          , bordered   = False
          , inverted   = False
          , pull       = Just (Right ())
          , animation  = Pulse
          }
        ]
      Fish
    ]
```


### Composition

It's fun to mix icons! The following program makes an icon stack:
```elm
import FontAwesome exposing (..)

view : model -> Html msg
view _
    = div []
    [ stylesheet
    , layers []
      [ LayerIcon    [] (Envelope Regular)
      , LayerCounter [] TopRight "42"
      ]
    ]
```

You can also make new icons by "cutting" them from one another:
<div class="fa-4x">
  <i class="fas fa-pencil-alt" data-fa-transform="shrink-10 up-.5" data-fa-mask="fas fa-comment" style="background:MistyRose"></i>
  <i class="fab fa-facebook-f" data-fa-transform="shrink-3.5 down-1.6 right-1.25" data-fa-mask="fas fa-circle" style="background:MistyRose"></i>
  <i class="fas fa-headphones" data-fa-transform="shrink-6" data-fa-mask="fas fa-square" style="background:MistyRose"></i>
</div>
```elm
import FontAwesome exposing (..)

view : model -> Html msg
view _
    = div []
    [ stylesheet
    , mask []
      FacebookF          -- cutout icon (see-thru)
      <| Circle Regular  -- outer icon (opaque)
    ]
```


## Elm-Icon Family
- [elm-ionicons](http://package.elm-lang.org/packages/surprisetalk/elm-ionicons/latest)
- [elm-font-awesome](http://package.elm-lang.org/packages/surprisetalk/elm-font-awesome/latest)
- [elm-material-icons](http://package.elm-lang.org/packages/surprisetalk/elm-material-icons/latest)
- [elm-open-iconic](http://package.elm-lang.org/packages/surprisetalk/elm-open-iconic/latest)

## Contributions
- Feel free to [report bugs on Github](https://github.com/surprisetalk/elm-icon/issues).
- If you have any suggestions on how to make the API more friendly, please reach out to me at [surprisetalk@gmail.com](surprisetalk@gmail.com).


# Elm-Font-Awesome

This package has a really easy-to-use API, with plenty of options!

It comes with a stylesheet and icons helpers:
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
icons : Html msg
icons
  = div []
    [ i [] Wrench
    , i [] InternetExplorer
    , i [] Briefcase
    ]
```


### Styling

Some styling shortcuts are included:
```elm
weirdSpinningCog : Html msg
weirdSpinningCog 
  = i [ bordered
      , fixedWidth
      , inverted
      , pullRight
      , spin
      , size Size.Large
      ]
   <| Cog Solid
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

weirdWand : Html Msg
weirdWand
  = i [ transform
        { scale  = Just <| Grow 17.1
        , shiftX = Just <| Left 25.5
        , shiftY = Just <| Down 12.9
        , rotate = Just <|      90.0
        }
      ]
    <| Magic Solid
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

stylishFish : Html msg
stylishFish
  = i [ style 
        { size     = Just X10
        , fixedWidth = True
        , bordered   = False
        , inverted   = False
        , pull     = Just (Right ())
        , animation  = Pulse
        }
      ]
    Fish
```


### Composition

It's fun to mix icons! The following program makes an icon stack:
```elm
unreadMessages : Html msg
unreadMessages
  = layers []
    [ LayerIcon    [] (Envelope Regular)
    , LayerCounter [] TopRight "42"
    ]
```

You can also make new icons by "cutting" them from one another:
```elm
customFB : Html msg
customFB
  = mask []
    FacebookF          -- cutout icon (see-thru)
    <| Circle Regular  -- outer icon (opaque)
```


## Elm-Icon Family
- [elm-ionicons](http:/package.elm-lang.org/packages/surprisetalk/elm-ionicons/latest)
- [elm-font-awesome](http:/package.elm-lang.org/packages/surprisetalk/elm-font-awesome/latest)
- [elm-material-icons](http:/package.elm-lang.org/packages/surprisetalk/elm-material-icons/latest)
- [elm-open-iconic](http:/package.elm-lang.org/packages/surprisetalk/elm-open-iconic/latest)

## Contributions
- Feel free to [report bugs on Github](https:/github.com/surprisetalk/elm-icon/issues).
- If you have any suggestions on how to make the API more friendly, please reach out to me at [surprisetalk@gmail.com](surprisetalk@gmail.com).

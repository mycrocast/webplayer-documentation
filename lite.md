# Webplayer Lite

## Adjust Player Elements
You can make adjustments to parts of the webplayer using CSS. The styles can be added via a ```<style>``` tag in the ```<body>```, or via an external stylesheet that is imported in the ```<head>```. Adjustments are made by setting CSS variables or by modifying shadow DOM parts. You can find fully implemented examples for both at the end of this page.

### Adjustment of colors using CSS variables

CSS variables can only be used to adjust the colors of the web player. Standard CSS colors, but also hexadecimal codes and RGBA colors can be used as colors. The following variables are defined:

|Variable|Explanation|
|----|----|
| mcc-player-background-color | Adjusts the background color of the entire player. |
| mcc-player-font-color | Adjusts the font color of the player, including all icons. |
| mcc-player-overlay-color | Adjusts the background color of the delay menu. |
| mcc-player-overlay-font-color | Changes the font color of the loading animation and of the delay menu, including all buttons for setting the delay. |
| mcc-player-button-disabled-color | Some buttons can be deactivated sometimes. By default, the color is set to grey, which can be changed using this variable. |
| mcc-player-delay-bar-background | Adjusts the background color of the delay bar in the delay menu |
| mcc-player-delay-bar-buffer | Adjusts the color of the indicator in the delay bar that shows the currently buffered audio data. Also affects the color of the "Live" button if no delay is set. |
| mcc-player-delay-bar-current | Adjusts the color of the indicator in the delay bar that represents the currently set delay. |

&nbsp;

The CSS style of the website should embed the variables similar to the following example:

```
mycrocast-lite-player {
    --mcc-player-background-color: #555555;
    --mcc-player-font-color: #ff2e2e;
	
    --mcc-player-overlay-color: #000000af;
    --mcc-player-overlay-font-color: #ff2e2e; 
	
    --mcc-player-button-disabled-color: #bb2222;
	
    --mcc-player-delay-bar-background: #bb2222;
    --mcc-player-delay-bar-buffer: #ff2e2e;
    --mcc-player-delay-bar-current: #ff8888;
}

```



Not all variables need to be defined.



&nbsp;

### Adjustments to other properties

A CSS class or a CSS shadow part can be overwritten as follows:

```
mcc-lite-player::part(mcc-lite-player-viewport) {
    /* define custom styles here */
}
```
  
Here, "mcc-lite-player-viewport" can be replaced by one of the class names defined on the following pages in order to customize various elements. The examples focus primarily on adjusting the colors, but any other CSS properties such as ```margin```, ```padding```, ```display```, ```position```, etc. can be defined for each class as required. Icons are interpreted as characters and can therefore be customized via ```font-size```, ```color```, etc.
&nbsp;

### mcc-lite-player-viewport

Can be used to adjust the height, width, color and shape of the player.

Example:

```
mcc-lite-player::part(mcc-lite-player-viewport) {
    background-color: #555555;
    height: 200px;
    border-radius: 0;
    width: 600px;
}
```

Result:

![image](https://github.com/mycrocast/webplayer-documentation/assets/82024455/a6aca57f-691a-4254-bd16-a56916ec8997)
&nbsp;

### mcc-play-pause-controls

Affects the play/pause icon on the left-hand side of the player. 

Example:

```
mcc-lite-player::part(mcc-play-pause-controls) {
    color: #ff2e2e;
    padding: 0 2em;
}
```

Result:

![image](https://github.com/mycrocast/webplayer-documentation/assets/82024455/b7edaf86-ea70-493b-ac03-223957387508)
&nbsp;

### mcc-play-pause-controls-disabled

If no live broadcast is available or advertisements are being played during an active broadcast, the play/pause button is deactivated and mcc-play-pause-controls is replaced by mcc-play-pause-controls-disabled. As the CSS class changes, all adjustments made for mcc-play-pause-controls must also be made for mcc-play-pause-controls-disabled! Only the color should be different to give the listener visual feedback that the button is disabled.

Example:

```
mcc-lite-player::part(mcc-play-pause-controls-disabled) {
    /*darker color to show that button is deactivated*/
    color: #bb2222;
	
    /*all other properties should be adopted!*/
    padding: 0 2em;
}
```

Result:

![image](https://github.com/mycrocast/webplayer-documentation/assets/82024455/a89e2eba-6cda-40dc-9622-80cdeffab4b4)
&nbsp;

### mcc-stream-title

Adjusts the properties of the stream title shown besides the play/pause-button.

Example:

```
mcc-lite-player::part(mcc-stream-title) {
    color: #ff2e2e;
}
```

Result:

![image](https://github.com/mycrocast/webplayer-documentation/assets/82024455/17ffc0a0-3c2d-47df-989d-8968099b050c)
&nbsp;

### mcc-listener-info

Adjusts the properties of the element containing the number of listeners. Affects both the icon and the displayed number. Can also be hidden with display: none if required.

Example:
```
mcc-lite-player::part(mcc-listener-info) {
    color: #ff2e2e;
 
    /*optional: can be hidden using the following code*/
    display: none;
}
```

Result (without hiding the element):

![image](https://github.com/mycrocast/webplayer-documentation/assets/82024455/5cf30be0-2290-4645-a9bd-27669ea78eea)
&nbsp;

### mcc-stream-info

Adjusts the properties of the other stream information (language and the stream start time).

Example:
```
mcc-lite-player::part(mcc-stream-info) {
    color: #ff2e2e;
}
```

Result:

![image](https://github.com/mycrocast/webplayer-documentation/assets/82024455/897be569-e9ac-41df-9dd6-9a0cad53bc95)
&nbsp;

### mcc-delay-overlay-button

Affects the icon on the right-hand side of the player that opens the synchronization menu.

Example:

```
mcc-lite-player::part(mcc-delay-overlay-button) {
    color: #ff2e2e;
}
```

Result:

![image](https://github.com/mycrocast/webplayer-documentation/assets/82024455/ad22090c-ce4e-4d15-a406-c38cfbd23d9c)
&nbsp;

### mcc-delay-overlay-button-disabled

Just like the play/pause button, the button for opening the delay menu is disabled in certain scenarios as well. The classes are exchanged here too, which is why all the properties set in mcc-delay-overlay-button must be adopted in mcc-delay-overlay-button-disabled. Only the color should also be changed here to give the listener visual feedback that the button is disabled.

Example:
```
mcc-lite-player::part(mcc-delay-overlay-button-disabled) {
    color: #bb2222;
}
```

Result:

![image](https://github.com/mycrocast/webplayer-documentation/assets/82024455/406a2a52-7967-4d05-8fe2-35fd260ea6db)
&nbsp;

### mcc-spot-item

When an advertisement is played, some elements in the player disappear and the user is shown the text "Advertisement - to be continued shortly". mcc-spot-item affects the element that contains this text.

Example:
```
mycrocast-lite-player::part(mcc-spot-item) {
    color: #ff2e2e;
}
```

Result:

![image](https://github.com/mycrocast/webplayer-documentation/assets/82024455/c32f8ff4-02b2-4072-8157-99669302e0e3)
&nbsp;

### mcc-message-info

The listener is occasionally shown status messages while listening, e.g. when the streamer is muted. The class customizes this status message.

Example:
```
mycrocast-lite-player::part(mcc-message-info) {
    color: #ff2e2e;
    background-color: white;
}
```
  
Result:

![image](https://github.com/mycrocast/webplayer-documentation/assets/82024455/2fbeacb5-aace-4c61-9b3c-458a55174b74)
&nbsp;

### mcc-message-danger

Displayed if there is a problem with the transmission. Behaves like mcc-message-info.

Example:
```
mycrocast-lite-player::part(mcc-message-danger) {
    color: white;
    background-color: darkred;
}
```

Result:

![image](https://github.com/mycrocast/webplayer-documentation/assets/82024455/de0ac353-635d-4245-b84a-e0165487f268)
&nbsp;

### mcc-stream-placeholder

Customizes to the element that is displayed when no transmission is available.

Example:
```
mycrocast-lite-player::part(mcc-stream-placeholder) {
    color: #ff2e2e;
}
```

Result:

![image](https://github.com/mycrocast/webplayer-documentation/assets/82024455/0ab2f272-437a-4b20-b7e8-41f9da9a9c94)
&nbsp;

### mcc-next-stream

If several streams are available, a button is displayed at the bottom of the player which the listener can use to navigate between different streams.

Example:
```
mycrocast-lite-player::part(mcc-next-stream) {
    color: #ff2e2e;
}
```

Result:

![image](https://github.com/mycrocast/webplayer-documentation/assets/82024455/4534190b-87b2-4f52-b01c-8e0e6944508d)
&nbsp;

### mcc-loading-anim-wrapper

Can be used to set the color, padding, and other properties of the laoding animation overlay

Example: 
```
mycrocast-lite-player::part(mcc-loading-anim-wrapper) {
    --color: #000000af;;
}
```

Result:

![image](https://github.com/mycrocast/webplayer-documentation/assets/82024455/020fd94f-0534-4dc8-81bd-5593cb3fc029)
&nbsp;

### mcc-loading-anim

Adjusts the properties of the loading animation within the loading animation wrapper.

Example:

```
mycrocast-lite-player::part(mcc-loading-anim) {
    --color: #ff2e2e;
}
```

Result:

![image](https://github.com/mycrocast/webplayer-documentation/assets/82024455/cd392355-22f7-4eb8-989e-48c4840b1e8e)
&nbsp;

### mcc-delay-overlay-wrapper

Can be used to set the color, padding, and other properties of the delay overlay

Example:
```
mycrocast-lite-player::part(mcc-delay-overlay-wrapper) {
    background-color: #000000af;
}
```

Result:

![image](https://github.com/mycrocast/webplayer-documentation/assets/82024455/e27a8c67-8c5f-4d38-aaaa-6338e75a8938)
&nbsp;

### mcc-delay-play-pause-controls

As the delay menu can have a different color, the play/pause button can also be different here. Can be customized like mcc-play-pause-controls.
```
mycrocast-lite-player::part(mcc-delay-play-pause-controls) {
    color: #ff2e2e;
}
```

Result:

![image](https://github.com/mycrocast/webplayer-documentation/assets/82024455/ba4019a7-5b96-4244-aad9-50c9e3534a95)
&nbsp;

### mcc-delay-play-pause-controls-disabled

The play/pause button can be deactivated in the delay menu as well. Again, all properties of mcc-delay-play-pause-controls should be adopted and only the color should be adjusted as visual indication.

Example:
```
mycrocast-lite-player::part(mcc-delay-play-pause-controls-disabled) {
    color: #bb2222;
}
```

![image](https://github.com/mycrocast/webplayer-documentation/assets/82024455/2cb32568-d284-409e-bbe7-da268f0de713)


&nbsp;
### mcc-delay-current

Adjusts the element containing the current delay in seconds in the delay menu.

Example:
```
mycrocast-lite-player::part(mcc-delay-current) {
    color: #ff2e2e;
}
```

Result:

![image](https://github.com/mycrocast/webplayer-documentation/assets/82024455/5d444a52-8130-437f-9c6b-31418ceb90d9)
&nbsp;

### mcc-delay-overlay-close

Adjusts the button that closes the delay menu.

Example:
```
mycrocast-lite-player::part(mcc-delay-overlay-close) {
    color: #ff2e2e;
}
```

Result:

![image](https://github.com/mycrocast/webplayer-documentation/assets/82024455/ee424885-42aa-4c5c-b30f-2b6bfe560d54)
&nbsp;

### mcc-delay-rewind-1s

Adjusts the button that increases the delay by one second. For the other buttons that set the delay, the classes are ```mcc-delay-rewind-5s```, ```mcc-delay-rewind-30s```, ```mcc-delay-forward-5s```, ```mcc-delay-forward-1s```, where "rewind" stands for increasing and "forward" for decreasing the delay.

Example for one of the buttons:
```
mycrocast-lite-player::part(mcc-delay-rewind-1s) {
    color: #ff2e2e;
}
``` 

Result:

![image](https://github.com/mycrocast/webplayer-documentation/assets/82024455/660b1e7e-c966-4779-811d-5dc0fdaee80d)
&nbsp;

### mcc-delay-to-live

Adjusts the button with the text "Live", which resets the delay to 0. To adjust the color, the variable ```--color``` must be set here!

Example:
```
mycrocast-lite-player::part(mcc-delay-to-live) {
    --color: #ff2e2e;
}
```

Result:

![image](https://github.com/mycrocast/webplayer-documentation/assets/82024455/0d8f45ea-ae17-402b-a12e-ab89ef67f798)
&nbsp;

### mcc-delay-bar-wrapper

Affects the delay bar in the delay menu as a whole. Can be used to define the background color and margins/paddings to other elements

&nbsp;
### mcc-delay-bar-buffered

Adjusts the indicator in the delay bar that shows how much audio data is currently buffered. Behaves similarly to mcc-delay-bar-wrapper

&nbsp;
### mcc-delay-bar-current

Adjusts the indicator in the delay bar that shows how long the current delay is. Behaves similarly to mcc-delay-bar-wrapper

Example editing all delay-bar classes:
```
mycrocast-lite-player::part(mcc-delay-bar-wrapper) {
    background-color: #bb2222;
}

mycrocast-lite-player::part(mcc-delay-bar-buffered) {
    background-color: #ff2e2e;
}

mycrocast-lite-player::part(mcc-delay-bar-current) {
    background-color: #ff8888;
}
```

Result:

![image](https://github.com/mycrocast/webplayer-documentation/assets/82024455/c756aa54-45bd-4044-aac3-b32a32f956ca)
&nbsp;

## Full Example with variables

Styles copied into a style tag within the ```<body>``` or imported from an external stylesheet in the ```<head>```:

```
<!doctype html>
<html>

<head>
<meta charset="utf-8">
<title>WebplayerLiteButton</title>
<base href="/">
<meta name="viewport" content="width=device-width, initial-scale=1">
<link rel="icon" type="image/x-icon" href="favicon.ico">
</head>

<body>
    <mycrocast-lite-player token="1567504890375_8741a554-c25e-428f-a807-a69bac373315-9999"></mycrocast-lite-player>
    <script id="mycrocast_base" src="https://mycrocast-webplayer.s3.eu-central-1.amazonaws.com/versioning-main.js" player=LITE_PLAYER></script>
    <style>

        mycrocast-lite-player {
            --mcc-player-background-color: #555555;  
            --mcc-player-font-color: #ff2e2e;  
  
            --mcc-player-overlay-color: #000000af;  
            --mcc-player-overlay-font-color: #ff2e2e;  
  
            --mcc-player-button-disabled-color: #bb2222;  
  
            --mcc-player-delay-bar-background: #bb2222;  
            --mcc-player-delay-bar-buffer: #ff2e2e;  
            --mcc-player-delay-bar-current: #ff8888;
        }
    </style>
</body>
</html>
```

### Resulting player:
![image](https://github.com/mycrocast/webplayer-documentation/assets/82024455/07f61725-385e-4759-b246-6bca1a7e31a4)

![image](https://github.com/mycrocast/webplayer-documentation/assets/82024455/17a0f28b-81b4-4984-87b2-9306724b5bb0)

![image](https://github.com/mycrocast/webplayer-documentation/assets/82024455/698a0df3-7ce2-4105-81d2-bf9894aac4ce)

![image](https://github.com/mycrocast/webplayer-documentation/assets/82024455/744979bb-d08d-4a9b-ab29-011527f794a1)

![image](https://github.com/mycrocast/webplayer-documentation/assets/82024455/9f1dbcda-f022-4148-bbf0-d5309979ba67)

![image](https://github.com/mycrocast/webplayer-documentation/assets/82024455/710251cb-8f8b-45cb-aa31-5285db993e57)

![image](https://github.com/mycrocast/webplayer-documentation/assets/82024455/98bcee20-ae42-47af-bbf6-406a796998fb)
&nbsp

## Full example with parts

```
<!doctype html>
<html>

<head>
<meta charset="utf-8">
<title>WebplayerLiteButton</title>
<base href="/">
<meta name="viewport" content="width=device-width, initial-scale=1">
<link rel="icon" type="image/x-icon" href="favicon.ico">
</head>

<body>
    <mycrocast-lite-player token="1567504890375_8741a554-c25e-428f-a807-a69bac373315-9999"></mycrocast-lite-player>
    <script
	    id="mycrocast_base"
	    src="https://mycrocast-webplayer.s3.eu-central-1.amazonaws.com/versioning-main.js"
	    player=LITE_PLAYER>
    </script>
    <style>
        mycrocast-lite-player::part(mcc-lite-player-viewport) {  
            background-color: #555555;  
            height: 200px;  
            border-radius: 0;  
            width: 600px;  
        }
  
        mycrocast-lite-player::part(mcc-play-pause-controls) {  
            color: #ff2e2e;  
            padding: 0 2em;  
        }  
  
        mycrocast-lite-player::part(mcc-play-pause-controls-disabled) {  
            /*different color to show that button is deactivated*/  
            color: #bb2222;  
  
            /*all other properties should be adopted!*/  
            padding: 0 2em;  
        }  
  
        mycrocast-lite-player::part(mcc-stream-title) {  
            color: #ff2e2e;  
        }  
  
        mycrocast-lite-player::part(mcc-listener-info) {  
            color: #ff2e2e;  
        }  
  
        mycrocast-lite-player::part(mcc-stream-info) {  
            color: #ff2e2e;  
        }  
  
        mycrocast-lite-player::part(mcc-delay-overlay-button) {  
            color: #ff2e2e;  
        }  
  
        mycrocast-lite-player::part(mcc-delay-overlay-button-disabled) {  
            color: #bb2222;  
        }  
  
        mycrocast-lite-player::part(mcc-spot-item) {  
            color: #ff2e2e;  
        }  
  
        mycrocast-lite-player::part(mcc-message-info) {  
            color: #ff2e2e;  
            background: white;  
        }  
  
        mycrocast-lite-player::part(mcc-message-danger) {  
            color: white;  
            background: darkred;  
        }  
  
        mycrocast-lite-player::part(mcc-stream-placeholder) {  
            color: #ff2e2e;  
        }

        mycrocast-lite-player::part(mcc-loading-anim-wrapper) {
            --color: #000000af;
        }

        mycrocast-lite-player::part(mcc-loading-anim) {
            --color: #ff2e2e;
        }
  
        mycrocast-lite-player::part(mcc-delay-overlay-wrapper) {  
            background-color: #000000af;  
        }  
  
        mycrocast-lite-player::part(mcc-delay-play-pause-controls) {  
            color: #ff2e2e;  
            padding: 0 2em;  
        }  
  
        mycrocast-lite-player::part(mcc-delay-play-pause-controls-disabled) {
            color: #bb2222;  
            padding: 0 2em;  
        }  
  
        mycrocast-lite-player::part(mcc-delay-current) {  
            color: #ff2e2e;  
        }  
  
        mycrocast-lite-player::part(mcc-delay-overlay-close) {  
            color: #ff2e2e;  
        }  
  
        mycrocast-lite-player::part(mcc-delay-rewind-1s) {  
            color: #ff2e2e;  
        }  
  
        mycrocast-lite-player::part(mcc-delay-rewind-5s) {  
            color: #ff2e2e;  
        }  
              
        mycrocast-lite-player::part(mcc-delay-rewind-30s) {  
            color: #ff2e2e;  
        }  
  
        mycrocast-lite-player::part(mcc-delay-to-live) {  
            --color: #ff2e2e;  
        }  
  
        mycrocast-lite-player::part(mcc-delay-forward-5s) {  
            color: #ff2e2e;  
        }  
  
        mycrocast-lite-player::part(mcc-delay-forward-1s) {  
            color: #ff2e2e;  
        }  
  
        mycrocast-lite-player::part(mcc-delay-bar-wrapper) {  
            background-color: #bb2222;  
            margin-left: 3em;  
        }  
  
        mycrocast-lite-player::part(mcc-delay-bar-buffered) {  
            background-color: #ff2e2e;  
        }  
  
        mycrocast-lite-player::part(mcc-delay-bar-current) {  
            background-color: #ff8888;  
            margin-left: 3em;  
        }  
  
        mycrocast-lite-player::part(mcc-next-stream) {  
            color: #ff2e2e;  
        }
    </style>
</body>
</html>
```

&nbsp;

### Resulting player:
![image](https://github.com/mycrocast/webplayer-documentation/assets/82024455/5ae3ff50-7e38-4f85-af9f-31fa7c5681cc)

![image](https://github.com/mycrocast/webplayer-documentation/assets/82024455/912cc8c9-4ab1-465c-8c51-062453efe345)

![image](https://github.com/mycrocast/webplayer-documentation/assets/82024455/d1e996fa-1af6-4932-b5cc-88788eec6087)

![image](https://github.com/mycrocast/webplayer-documentation/assets/82024455/301f7496-c429-4735-998f-cfde6eb284d3)

![image](https://github.com/mycrocast/webplayer-documentation/assets/82024455/0fc77cdb-69ff-4451-944f-4bd220fbff9d)

![image](https://github.com/mycrocast/webplayer-documentation/assets/82024455/0b0f71c1-1d8b-44e2-b536-71705540a78c)

![image](https://github.com/mycrocast/webplayer-documentation/assets/82024455/5cb8fe20-ce9a-4f4c-b245-51f29f4a808e)

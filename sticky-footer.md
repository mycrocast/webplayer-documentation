# Floating-Button Webplayer

## Adjust Player Elements
You can make adjustments to parts of the webplayer using CSS. The styles can be added via a ```<style>``` tag in the ```<body>```, or via an external stylesheet that is imported in the ```<head>```. Adjustments are made by setting CSS variables or by modifying shadow DOM parts. You can find fully implemented examples for both at the end of this page.

### Adjustment of colors using CSS variables

CSS variables can only be used to adjust the colors of the web player. Standard CSS colors, but also hexadecimal codes and RGBA colors can be used as colors. The following variables are defined:

|Variable|Explanation|
|----|----|
| mcc-player-background-color | Adjusts the background color of the button and the content view. |
| mcc-player-font-color | Adjusts the font color of the player, including all icons. Also sets the color of the border of the content view. |
| mcc-player-overlay-color | Adjusts the background color of the loading overlay and the spot overlay. |
| mcc-player-overlay-font-color | Adjusts the animation color in the loading overlay and the font color of the spot overlay|
| mcc-player-button-disabled-color | Adjusts the color of disabled buttons in the player. |
| mcc-player-delay-bar-background | Adjusts the background color of the delay bar in the delay menu |
| mcc-player-delay-bar-buffer | Adjusts the color of the indicator in the delay bar that shows the currently buffered audio data. Also affects the color of the "Live" button. |
| mcc-player-delay-bar-current | Adjusts the color of the indicator in the delay bar that represents the currently set delay. |

The CSS style of the website should embed the variables similar to the following example:

```
mycrocast-sticky-footer-player {
    --mcc-player-background-color: #555555;  
    --mcc-player-font-color: #ff2e2e;
	  
	--mcc-player-overlay-color: #ffffffaf;  
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
mycrocast-sticky-footer-player::part(mcc-player-initial-button) {
    /* define custom styles here */
}
```
  
Here, ```mcc-player-initial-button``` can be replaced by one of the class names defined on the following pages in order to customize various elements. The examples focus primarily on adjusting the colors, but any other CSS properties such as ```margin```, ```padding```, ```display```, ```position```, ```width```, etc. can be defined for each class as required. Icons are interpreted as characters and can therefore be customized via ```font-size```, ```color```, etc.

### mcc-player-initial-button
Adjusts the properties of the button shown initially when a stream is available. The class can be used to change its size as well. When the stream title is too long for the button to contain it, it will be cut off and replaced with "..." at the end of the element.

Example:
```
mycrocast-floating-button-player::part(mcc-player-initial-button) {  
    background-color: #555555;
    width: 16em;
    height: 5em;
    border: 2px solid #ff2000;
	font-size: 3em;
}
```

Some properties, like ```padding``` and ```gap```, as well as the mycrocast logo, are scaled automatically by setting the ```font-size``` property. This simplifies the styling process, but you can also override this behavior by setting the properties that are dependent on the ```font-size```.

### mcc-player-initial-button
Can be used to additionally style the element containing the stream title within the initial button. Optionally, you can also disable the element so only the mycrocast logo is shown, resulting in less screen space taken by the initial button.

Result:

![image](https://github.com/mycrocast/webplayer-documentation/assets/82024455/b977504c-eff1-46d1-a651-e4347f33ff8a)
&nbsp;

### mcc-player-content-wrapper
Adjusts the properties of the stream view after the listener clicked on the initial button. The class can be used to change the dimensions of the stream view as well.

Example:
```
mycrocast-floating-button-player::part(mcc-player-content-wrapper) {  
    background-color: #555555;
    border-color: #ff2000;
    border: 2px solid #ff2000;
}
```

Result:

![image](https://github.com/mycrocast/webplayer-documentation/assets/82024455/3acba4d3-c6d5-4c45-8f42-7d0bd2d2a093)
&nbsp;

### mcc-stream-title
Adjusts the properties of the stream title.

Example:
```
mycrocast-floating-button-player::part(mcc-stream-title) {
    color: #ff2000;
}
```

Result:

![image](https://github.com/mycrocast/webplayer-documentation/assets/82024455/0a41b261-d5c3-4a2e-81b6-84698da4357b)
&nbsp;

### mcc-stream-language
Adjusts the properties of the stream language.

Example:
```
mycrocast-floating-button-player::part(mcc-stream-language) {
    color: #ff2000;
}
```

Result:

![image](https://github.com/mycrocast/webplayer-documentation/assets/82024455/9b01666b-6391-475b-b8d1-9be22ddca908)
&nbsp;

### mcc-listener-count
Adjusts the properties of the listener icon, the listener count and the dash between the language and the listener-icon.

Example:
```
mycrocast-floating-button-player::part(mcc-listener-count) {
    color: #ff2000;
}
```

Result:

![image](https://github.com/mycrocast/webplayer-documentation/assets/82024455/3d6c811a-a22f-49b4-a64b-351b5f86b6bc)
&nbsp;

### mcc-play-pause-controls
Changes the properties of the play/pause-button within the stream view. Affects both the icon and the text besides it.

Example:
```
mycrocast-floating-button-player::part(mcc-play-pause-controls) {  
    color: #ff2000;  
}
```

Result:

![image](https://github.com/mycrocast/webplayer-documentation/assets/82024455/2acfa4e6-5ee4-421e-9ff2-0b1956c15a9c)
&nbsp;

### mcc-stop-listen-button
Changes the property of the stop-listen-button within the stream view. Affects both the icon and the text besides it.

Example:

```
mycrocast-floating-button-player::part(mcc-stop-listen-button) {  
    color: #ff2000;  
}
```

Result:

![image](https://github.com/mycrocast/webplayer-documentation/assets/82024455/0b54115d-05df-47f2-bc41-ffb94ef961f5)
&nbsp;

### mcc-next-stream-button
Changes the properties of the next-stream-button within the stream view. Affects both the icon and the text besides it.

Example:
```
mycrocast-floating-button-player::part(mcc-next-stream-button) {  
    color: #ff2000;  
}
```

Result:

![image](https://github.com/mycrocast/webplayer-documentation/assets/82024455/7265a2ad-92af-474d-a0ca-4e3fda246bc7)
&nbsp;

### mcc-spot-item
Changes the properties of the spot title and the text "to be continued shortly" when a spot is being played.

Example:
```
mycrocast-floating-button-player::part(mcc-spot-item) {  
    color: #ff2000;  
}
```

Result:

![image](https://github.com/mycrocast/webplayer-documentation/assets/82024455/e7621c4a-3a89-4a5f-a2cf-071c5dadb9d7)

&nbsp;

### mcc-player-content-close
Changes the properties of the close icon on the top right of the stream view.

Example:
```
mycrocast-floating-button-player::part(mcc-player-content-close) {  
    color: #ff2000;  
}
```

Result:

![image](https://github.com/mycrocast/webplayer-documentation/assets/82024455/08070079-0081-4371-a1a6-5364512d7250)

&nbsp;

### mcc-message-info
The listener is occasionally shown status messages while listening, e.g. when the streamer is muted. The class customizes this status message.

Example:
```
mycrocast-floating-button-player::part(mcc-message-info) {  
    color: #ff2000;  
    background: white;  
}
```

Result:

![image](https://github.com/mycrocast/webplayer-documentation/assets/82024455/29199e60-4798-42cd-b829-ae739af51f93)
&nbsp;

### mcc-message-danger
Displayed if there is a problem with the transmission. Behaves like mcc-message-info.

Example:
```
mycrocast-floating-button-player::part(mcc-message-danger) {  
    color: white;  
    background: darkred;  
}
```

Result:

![image](https://github.com/mycrocast/webplayer-documentation/assets/82024455/4a56bdfe-77d5-428a-8140-fb354f849fd0)
&nbsp;

### mcc-delay-current
Adjusts properties of the element displaying the current delay in seconds besides the delay bar.

Example:
```
mycrocast-floating-button-player::part(mcc-delay-current) {  
    color: #ff2000;  
}
```

Result:

![image](https://github.com/mycrocast/webplayer-documentation/assets/82024455/cd5ca8ef-7db2-4c49-8f00-a96b4edf70e8)

&nbsp;

### mcc-delay-rewind-1s
Adjusts the button that increases the delay by one second. For the other buttons that set the delay, the classes are ```mcc-delay-rewind-5s```, ```mcc-delay-rewind-30s```, ```mcc-delay-forward-5s```, ```mcc-delay-forward-1s```, where "rewind" stands for increasing and "forward" for decreasing the delay.

Example for one of the buttons:
```
mycrocast-floating-button-player::part(mcc-delay-rewind-1s) {  
    color: black;  
}
```

Result:

![image](https://github.com/mycrocast/webplayer-documentation/assets/82024455/bf8456cf-0174-49de-b4f8-934e7ed4ee1b)
&nbsp;

### mcc-delay-to-live

Adjusts the button with the text "Live", which resets the delay to 0. To adjust the color, the variable ```--color``` must be set here!

Example:
```
mycrocast-floating-button-player::part(mcc-delay-to-live) {
    --color: #ff2000;
}
```

Result:

![image](https://github.com/mycrocast/webplayer-documentation/assets/82024455/e580fa31-abe0-474b-9411-051c266fd2c1)


### mcc-delay-bar-wrapper

Affects the delay bar in the delay menu as a whole. Can be used to define the background color and margins/paddings to other elements
&nbsp;

### mcc-delay-bar-buffered

Adjusts the indicator in the delay bar that shows how much audio data is currently buffered. Behaves similarly to mcc-delay-bar-wrapper
&nbsp;

### mcc-delay-bar-current
Adjusts the indicator in the delay bar that shows how long the current delay is. Behaves similarly to mcc-delay-bar-wrapper
&nbsp;

Example editing all delay-bar-classes:
```
mycrocast-floating-button-player::part(mcc-delay-bar-wrapper) {
    background-color: #bb2222;
}

mycrocast-floating-button-player::part(mcc-delay-bar-buffered) {
    background-color: #ff2000;
}

mycrocast-floating-button-player::part(mcc-delay-bar-current) {
    background-color: #ff8888;
}
```

Result:

![image](https://github.com/mycrocast/webplayer-documentation/assets/82024455/15ef8245-575b-497d-9281-9a80fbba14e6)
&nbsp;

## Full example with variables
The following code snippet shows an example HTML page that embeds the player and adjusts its properties using CSS variables:

```
<!doctype html>
<html>

<head>
<meta charset="utf-8">
<title>WebplayerStickyFooter</title>
<base href="/">
<meta name="viewport" content="width=device-width, initial-scale=1">
<link rel="icon" type="image/x-icon" href="favicon.ico">
</head>

<body>
    <mycrocast-sticky-footer-player token="1567504890375_8741a554-c25e-428f-a807-a69bac373315-9999"></mycrocast-sticky-footer-player>
    <script id="mycrocast_base" src="https://mycrocast-webplayer.s3.eu-central-1.amazonaws.com/versioning-main.js" player=STICKY_FOOTER_PLAYER></script>
    <style>

        mycrocast-sticky-footer-player {
            --mcc-player-background-color: #555555;  
            --mcc-player-font-color: #ff2e2e;
	  
	        --mcc-player-overlay-color: #ffffffaf;  
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

### Result:

![image](https://github.com/user-attachments/assets/7c76821b-4fc2-4959-b1af-5d4ad8271ccb)
![image](https://github.com/user-attachments/assets/33b5ef2b-d635-4dcb-ac9f-08bf88ae2c14)
![image](https://github.com/user-attachments/assets/592e6a69-7c52-4808-8870-9780e150e6f1)
![image](https://github.com/user-attachments/assets/616e961e-5558-4db2-8fab-7faa4b35a7a3)


&nbsp;

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
    <mycrocast-floating-button-player token="1567504890375_8741a554-c25e-428f-a807-a69bac373315-9999"></mycrocast-floating-button-player>
    <script id="mycrocast_base" src="https://mycrocast-webplayer.s3.eu-central-1.amazonaws.com/versioning-main.js" player=FLOATING_BUTTON_PLAYER></script>
    <style>
        mycrocast-floating-button-player::part(mcc-player-initial-button) {  
            background-color: #555555;  
            width: 5em;  
            height: 5em;  
            border: 2px solid #ff2000;  
        }  
  
        mycrocast-floating-button-player::part(mcc-player-content-wrapper) {  
            background-color: #555555;  
            border-color: #ff2000;  
            border: 2px solid #ff2000;  
        }  
  
        mycrocast-floating-button-player::part(mcc-stream-title) {  
            color: #ff2000;  
        }  
  
        mycrocast-floating-button-player::part(mcc-listener-count) {  
            color: #ff2000;  
        }  
  
        mycrocast-floating-button-player::part(mcc-stream-language) {  
            color: #ff2000;  
        }  
  
        mycrocast-floating-button-player::part(mcc-play-pause-controls) {  
            color: #ff2000;  
        }  
  
        mycrocast-floating-button-player::part(mcc-stop-listen-button) {  
            color: #ff2000;  
        }  
  
        mycrocast-floating-button-player::part(mcc-spot-item) {  
            color: #ff2000;  
        }  
  
        mycrocast-floating-button-player::part(mcc-next-stream-button) {  
            color: #ff2000;  
        }  
  
        mycrocast-floating-button-player::part(mcc-player-content-close) {  
            color: #ff2000;  
        }  
  
        mycrocast-floating-button-player::part(mcc-message-info) {  
            color: #ff2000;  
            background: white;  
        }  
  
        mycrocast-floating-button-player::part(mcc-message-danger) {  
            color: white;  
            background: darkred;  
        }  
  
  
        mycrocast-floating-button-player::part(mcc-delay-current) {  
            color: #ff2000;  
        }  
  
        mycrocast-floating-button-player::part(mcc-delay-rewind-1s) {  
            color: #ff2000;  
        }  
  
        mycrocast-floating-button-player::part(mcc-delay-rewind-5s) {  
            color: #ff2000;  
        }  
  
        mycrocast-floating-button-player::part(mcc-delay-rewind-30s) {  
            color: #ff2000;  
        }  
  
        mycrocast-floating-button-player::part(mcc-delay-to-live) {  
            --color: #ff2000;  
        }  
  
        mycrocast-floating-button-player::part(mcc-delay-forward-5s) {  
            color: #ff2000;  
        }  
  
        mycrocast-floating-button-player::part(mcc-delay-forward-1s) {  
            color: #ff2000;  
        }  
  
        mycrocast-floating-button-player::part(mcc-delay-bar-wrapper) {  
            background-color: #bb2222;  
        }  
  
        mycrocast-floating-button-player::part(mcc-delay-bar-buffered) {  
            background-color: #ff2000;  
        }  
  
        mycrocast-floating-button-player::part(mcc-delay-bar-current) {  
            background-color: #ff8888;  
        }
    </style>
</body>
</html>
```

### Resulting player:

![image](https://github.com/mycrocast/webplayer-documentation/assets/82024455/27246203-39e6-47fe-8ee7-d2e3f4631dce)

![image](https://github.com/mycrocast/webplayer-documentation/assets/82024455/a362cbf1-4368-4b16-91e8-f2e5c8cb3352)

![image](https://github.com/mycrocast/webplayer-documentation/assets/82024455/e2ab440f-7757-4cde-b5f4-d094dd98f146)

![image](https://github.com/mycrocast/webplayer-documentation/assets/82024455/c5427e73-75c4-4d2b-a3be-7c6dfd2baba9)


# Sticky-Footer Webplayer

## Adjust Player Elements
You can make adjustments to parts of the webplayer using CSS. The styles can be added via a ```<style>``` tag in the ```<body>```, or via an external stylesheet that is imported in the ```<head>```. Adjustments are made by setting CSS variables or by modifying shadow DOM parts. You can find fully implemented examples for both at the end of this page.

### Adjustment of colors using CSS variables

The following CSS variables can only be used to adjust the colors of the web player. Standard CSS colors, but also hexadecimal codes and RGBA colors can be used as colors. The following variables are defined:

|Variable|Explanation|
|----|----|
| mcc-player-background-color | Adjusts the background color of the button and the stream view. |
| mcc-player-font-color | Adjusts the font color of the player, including all icons. |
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
    --mcc-player-font-color: #ff2000;
	  
    --mcc-player-overlay-color: #ffffffaf;  
    --mcc-player-overlay-font-color: #ff2e2e;  
  
    --mcc-player-button-disabled-color: #bb2222;
  
    --mcc-player-delay-bar-background: #bb2222;  
    --mcc-player-delay-bar-buffer: #ff2000;  
    --mcc-player-delay-bar-current: #ff8888;
}
```  

Not all variables need to be defined.

&nbsp;

### Adjustments to other properties

#### Default styles

A CSS class or a CSS shadow part can be overwritten as follows:

```
mycrocast-sticky-footer-player::part(mcc-player-initial-button) {
    /* define custom styles here */
}
```
  
Here, ```mcc-player-initial-button``` can be replaced by one of the class names defined on the following pages in order to customize various elements. The examples focus primarily on adjusting the colors, but any other CSS properties such as ```margin```, ```padding```, ```display```, ```position```, ```width```, etc. can be defined for each class as required. Icons are interpreted as characters and can therefore be customized via ```font-size```, ```color```, etc.

#### Responsive styles

In order to render the player correctly on mobile devices, some of the provided CSS shadow parts change their behaviour based on screen size. You can change their behaviour by making use of media queries.

Example:
```
@media screen and (max-width: 992px) {
    mycrocast-sticky-footer-player::part(mcc-player-initial-button) {
        /* define custom styles for screens with a width smaller than 992px here */
    }
}
```

### mcc-player-initial-button
Adjusts the properties of the button shown initially when a stream is available. The class can be used to change its size as well. When the stream title is too long for the button to contain it, it will be cut off and replaced with "..." at the end of the element.

Example:
```
mycrocast-floating-button-player::part(mcc-player-initial-button) {  
    background-color: #555555;
    width: 30rem;
    border: 2px solid #ff2000;
    font-size: 3em;
}
```

Some properties, like ```padding``` and ```gap```, as well as the mycrocast logo, are scaled automatically by setting the ```font-size``` property. This simplifies the styling process, but you can also override this behavior by setting the properties that are dependent on the ```font-size```.

Result:

![image](https://github.com/user-attachments/assets/ca0ec548-1e94-4342-84ff-6208b201d421)


### mcc-player-initial-button-title
Can be used to additionally style the element containing the stream title within the initial button. Optionally, you can also disable the element so only the mycrocast logo is shown, resulting in less screen space taken by the initial button.

Example:
```
mycrocast-sticky-footer-player::part(mcc-player-initial-button) {
    background-color: #555555;
    border: 2px solid #ff2000;
    font-size: 3em;
}

mycrocast-sticky-footer-player::part(mcc-player-initial-button-title) {  
    display: none;
}
```

Result:
![image](https://github.com/user-attachments/assets/a6ff9271-8ab8-4f66-9c38-4dd7f3ca4829)


### mcc-player-content-wrapper
Adjusts the properties of the stream view after the listener clicked on the initial button. The class can be used to change the dimensions of the stream view as well.

When you change the ```padding``` properties of the stream view, keep in mind that the default behaviour changes these properties depending on the screen size. You can overwrite this by using media queries with the according breakpoints at 425px and 1400px screen width.

Example:
```
mycrocast-sticky-footer-player::part(mcc-player-content-wrapper) {    
    background-color: #555555;  
}
```

Result:
![image](https://github.com/user-attachments/assets/1223da39-4399-45d7-89d1-a4bdd6c29cc3)

&nbsp;

### mcc-player-volume-button
**NOTE: This button is currently not available and will not be shown in the stream view. It will be available in a future update.**

Adjusts the properties of the button that opens the volume slider when clicking on it.

Example:
```
mycrocast-sticky-footer-player::part(mcc-player-volume-button) {  
    color: #ff2000;  
}
```

Result:
![image](https://github.com/user-attachments/assets/28a01d65-88de-4c6e-bd9a-282d209305e8)

&nbsp;

### mcc-player-volume-slider
**NOTE: Just like the button, the volume slider is currently not available and will not be shown in the stream view. It will be available in a future update.**

Adjusts the properties of the slider that opens when clicking on the volume button.

Example:
```
mycrocast-sticky-footer-player::part(mcc-player-volume-slider) {  
    --color: #ff2000;
    background-color: #555555;
}
```

Result:
![image](https://github.com/user-attachments/assets/512604aa-7605-4ca0-9b4d-4f7569470ead)
&nbsp;

### mcc-stream-title
Adjusts the properties of the stream title and the stream language, shown besides the volume button.

Example:
```
mycrocast-sticky-footer-player::part(mcc-stream-title) {
    color: #ff2000;
}
```
Result:

![image](https://github.com/user-attachments/assets/191cbf1e-44b5-4d0e-a392-9fc2aa494ffd)

&nbsp;

### mcc-next-stream-button

Adjusts the properties of the next-stream button, which is shown when multiple streams are available. This button will move below the stream title and language on screens that are not wider than 992px.

```
mycrocast-sticky-footer-player::part(mcc-player-next-stream-button) {  
    color: #ff2000;  
}
```

Result:

![image](https://github.com/user-attachments/assets/f73053c6-1ca7-4101-bba4-62d0402f51ce)
&nbsp;

### mcc-delay-current
Adjusts properties of the element displaying the current delay in seconds besides the delay bar.

Example:
```
mycrocast-sticky-footer-player::part(mcc-delay-current) {  
    color: #ff2000;  
}
```

Result:

![image](https://github.com/user-attachments/assets/580d01eb-bbc7-4908-b9a2-7158cb11ae8d)
&nbsp;

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
mycrocast-sticky-footer-player::part(mcc-delay-bar-wrapper) {
    background-color: #bb2222;
}

mycrocast-sticky-footer-player::part(mcc-delay-bar-buffered) {
    background-color: #ff2000;
}

mycrocast-sticky-footer-player::part(mcc-delay-bar-current) {
    background-color: #ff8888;
}
```

Result:

![image](https://github.com/user-attachments/assets/66d793bd-79ab-4ccd-95dd-053c4293a1c2)
&nbsp;

### mcc-delay-to-live

Adjusts the button with the text "Live", which resets the delay to 0. To adjust the color, the variable ```--color``` must be set here!

Example:
```
mycrocast-sticky-footer-player::part(mcc-delay-to-live) {
    --color: #ff2000;
}
```

Result:

![image](https://github.com/user-attachments/assets/1fbe6565-cab3-4ea9-9a46-0666fd29632e)
&nbsp;


### mcc-delay-rewind-1s
Adjusts the button that increases the delay by one second. For the other buttons that set the delay, the classes are ```mcc-delay-rewind-5s```, ```mcc-delay-rewind-30s```, ```mcc-delay-forward-5s```, ```mcc-delay-forward-1s```, where "rewind" stands for increasing and "forward" for decreasing the delay.

Example for one of the buttons:
```
mycrocast-sticky-footer-player::part(mcc-delay-rewind-1s) {  
    color: #ff2000;  
}
```

Result:

![image](https://github.com/user-attachments/assets/1d05f6b1-dc3c-4082-b3f3-110dee2f2ea5)
&nbsp;


### mcc-play-pause-controls
Changes the properties of the play/pause-button within the stream view.

Example:
```
mycrocast-sticky-footer-player::part(mcc-play-pause-controls) {  
    color: #ff2000;  
}
```

Result:

![image](https://github.com/user-attachments/assets/a74df488-0a02-496f-bcc6-dc124d5a0684)

&nbsp;

### mcc-minimize-player-button
Changes the properties of the close icon on the top right of the stream view.

Example:
```
mycrocast-sticky-footer-player::part(mcc-minimize-player-button) {  
    color: #ff2000;  
}
```

Result:

![image](https://github.com/user-attachments/assets/cbaf1165-8163-4938-ad16-61893097f864)


&nbsp;


### mcc-spot-overlay
Changes the properties of the spot title and the text "to be continued shortly" when a spot is being played.

Example:
```
mycrocast-sticky-footer-player::part(mcc-spot-item) {  
    color: #ff2000;  
}
```

Result:

![image](https://github.com/user-attachments/assets/94764870-68ef-408b-b0ef-6a71377ba688)


&nbsp;

### mcc-message-info
The listener is occasionally shown status messages while listening, e.g. when the streamer is muted. The class customizes this status message.

Example:
```
mycrocast-sticky-footer-player::part(mcc-message-info) {  
    color: #ff2000;  
    background: white;  
}
```

Result:

![image](https://github.com/user-attachments/assets/b660c22c-879d-43c3-be0d-a9d5955fd622)

&nbsp;

### mcc-message-danger
Displayed if there is a problem with the transmission. Behaves like mcc-message-info.

Example:
```
mycrocast-sticky-footer-player::part(mcc-message-danger) {  
    color: white;  
    background: darkred;  
}
```

Result:

![image](https://github.com/user-attachments/assets/943d88ca-e07f-49db-a907-91b17b2bddc0)

&nbsp;


### mcc-loading-wrapper

Adjusts the properties of the loading overlay, displayed when the player itself is loading, or the connection to a stream is established.

Example:
```
mycrocast-sticky-footer-player::part(mcc-loading-wrapper) {
    background: #ffffffaa;  
}
```

Result:

![image](https://github.com/user-attachments/assets/7b80da00-9505-4df7-9e3f-f569c5e305c5)

&nbsp;

### mcc-loading-animation

Adjusts the properties of the loading overlay, displayed when the player itself is loading, or the connection to a stream is established.

Example:
```
mycrocast-sticky-footer-player::part(mcc-loading-animation) {
    background: #ff2000;  
}
```

Result:

![image](https://github.com/user-attachments/assets/080bb303-2f5e-418b-ab13-408e997ec2f9)

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
            --mcc-player-font-color: #ff2000;
	  
            --mcc-player-overlay-color: #ffffffaf;  
            --mcc-player-overlay-font-color: #ff2e2e;  
   
            --mcc-player-button-disabled-color: #bb2222;
  
            --mcc-player-delay-bar-background: #bb2222;  
            --mcc-player-delay-bar-buffer: #ff2000;  
            --mcc-player-delay-bar-current: #ff8888;
}
    </style>
</body>
</html>
```

### Result:

![image](https://github.com/user-attachments/assets/d95e70bd-f26f-49e3-84f9-a64381cbff79)

![image](https://github.com/user-attachments/assets/360d4bc8-82bf-46b3-8e1e-59fde4562aef)

![image](https://github.com/user-attachments/assets/8aa9533b-a64a-475b-8377-9ac90c97682d)

![image](https://github.com/user-attachments/assets/1312a546-829f-4201-9d83-0621bc8e4a43)

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
    <mycrocast-sticky-footer-player token="1567504890375_8741a554-c25e-428f-a807-a69bac373315-9999"></mycrocast-sticky-footer-player>
    <script id="mycrocast_base" src="https://mycrocast-webplayer.s3.eu-central-1.amazonaws.com/versioning-main.js" player=STICKY_FOOTER_PLAYER></script>
    <style>
        mycrocast-sticky-footer-player::part(mcc-player-initial-button) {  
            background-color: #555555;  
            border: 2px solid #ff2000;  
            font-size: 3em;  
        }  
  
        mycrocast-sticky-footer-player::part(mcc-player-initial-button-title) {  
            display: none;  
            font-size: 1em;  
        }  
  
        mycrocast-sticky-footer-player::part(mcc-player-content-wrapper) {  
            background-color: #555555;  
        }  
  
        mycrocast-sticky-footer-player::part(mcc-player-volume-button) {  
            color: #ff2000;  
        }  
  
        mycrocast-sticky-footer-player::part(mcc-player-volume-slider) {  
            --color: #ff2000;  
            background-color: #555555;  
        }  
  
        mycrocast-sticky-footer-player::part(mcc-stream-title) {  
            color: #ff2000;  
        }  
  
        mycrocast-sticky-footer-player::part(mcc-stream-language) {  
            color: #ff2000;  
        }  
  
        mycrocast-sticky-footer-player::part(mcc-player-next-stream-button) {  
            color: #ff2000;  
        }  
  
        mycrocast-sticky-footer-player::part(mcc-delay-current) {  
            color: #ff2000;  
        }  
  
        mycrocast-sticky-footer-player::part(mcc-delay-bar-wrapper) {  
            background-color: #bb2222;  
        }  
  
        mycrocast-sticky-footer-player::part(mcc-delay-bar-buffered) {  
            background-color: #ff2000;  
        }  
  
        mycrocast-sticky-footer-player::part(mcc-delay-bar-current) {  
            background-color: #ff8888;  
        }  
  
        mycrocast-sticky-footer-player::part(mcc-delay-to-live) {  
            --color: #ff2000;  
        }  
  
        mycrocast-sticky-footer-player::part(mcc-delay-rewind-30s) {  
            color: #ff2000;  
        }  
  
        mycrocast-sticky-footer-player::part(mcc-delay-rewind-5s) {  
            color: #ff2000;  
        }  
  
        mycrocast-sticky-footer-player::part(mcc-delay-rewind-1s) {  
            color: #ff2000;  
        }  
  
        mycrocast-sticky-footer-player::part(mcc-delay-forward-1s) {  
            color: #ff2000;  
        }  
  
        mycrocast-sticky-footer-player::part(mcc-delay-forward-5s) {  
            color: #ff2000;  
        }  
  
        mycrocast-sticky-footer-player::part(mcc-play-pause-controls) {  
            color: #ff2000;  
        }  
  
        mycrocast-sticky-footer-player::part(mcc-minimize-player-button) {  
            color: #ff2000;  
        }  
  
        mycrocast-sticky-footer-player::part(mcc-spot-overlay) {  
            color: #ff2000;  
            background-color: #ffffffaa;  
        }  
  
        mycrocast-sticky-footer-player::part(mcc-message-info) {  
            color: #ff2000;  
            background: white;  
        }  
  
        mycrocast-sticky-footer-player::part(mcc-message-danger) {  
            color: white;  
            background: darkred;  
        }  
  
        mycrocast-sticky-footer-player::part(mcc-loading-wrapper) {  
            background: #ffffffaa;  
        }  
  
        mycrocast-sticky-footer-player::part(mcc-loading-animation) {  
            --color: #ff2000;  
        }
    </style>
</body>
</html>
```

### Resulting player:

![image](https://github.com/user-attachments/assets/84415576-9176-486d-bb79-f8aabf694ba5)

![image](https://github.com/user-attachments/assets/13adf069-7273-48f2-97fc-f7400bc645c8)

![image](https://github.com/user-attachments/assets/07ff53dc-0cd8-4c32-9cec-37fff5062940)

![image](https://github.com/user-attachments/assets/d0b663c8-f61a-4729-a3ee-ad6b1a764b26)

![image](https://github.com/user-attachments/assets/8cbe268e-05e1-42d0-b371-f881d8f9da38)

![image](https://github.com/user-attachments/assets/8ac8de21-c418-4803-bd8f-c829f9de721a)



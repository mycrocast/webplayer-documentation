# Floating-Button Webplayer

## Adjust Player Elements
You can make adjustments to parts of the webplayer using CSS. The styles can be added via a ```<style>``` tag in the ```<body>```, or via an external stylesheet that is imported in the ```<head>```. Adjustments are made by setting CSS variables or by modifying shadow DOM parts. You can find fully implemented examples for both at the end of this page.

### Adjustment of colors using CSS variables

CSS variables can only be used to adjust the colors of the web player. Standard CSS colors, but also hexadecimal codes and RGBA colors can be used as colors. The following variables are defined:

|Variable|Explanation|
|----|----|
| mcc-player-background-color | Adjusts the background color of the button and the content view. |
| mcc-player-font-color | Adjusts the font color of the player, including all icons. Also sets the color of the border of the content view. |
| mcc-player-delay-bar-background | Adjusts the background color of the delay bar in the delay menu |
| mcc-player-delay-bar-buffer | Adjusts the color of the indicator in the delay bar that shows the currently buffered audio data. Also affects the color of the "Live" button. |
| mcc-player-delay-bar-current | Adjusts the color of the indicator in the delay bar that represents the currently set delay. |

The CSS style of the website should embed the variables similar to the following example:

```
mycrocast-floating-button-player {
    --mcc-player-background-color: red;
    --mcc-player-font-color: white;
	
    --mcc-player-delay-bar-background: darkblue;
    --mcc-player-delay-bar-buffer: blue;
    --mcc-player-delay-bar-current: lightblue;
}

```  

Not all variables need to be defined.

&nbsp;

### Adjustments to other properties

A CSS class or a CSS shadow part can be overwritten as follows:

```
mcc-floating-button-player::part(mcc-player-initial-button) {
    /* define custom styles here */
}
```
  
Here, ```mcc-player-initial-button``` can be replaced by one of the class names defined on the following pages in order to customize various elements. The examples focus primarily on adjusting the colors, but any other CSS properties such as ```margin```, ```padding```, ```display```, ```position```, ```width```, etc. can be defined for each class as required. Icons are interpreted as characters and can therefore be customized via ```font-size```, ```color```, etc.

#### mcc-player-initial-button
Adjusts the properties of the button shown initially when a stream is available. The class can be used to change its size as well.
```
mycrocast-floating-button-player::part(mcc-player-initial-button) {  
    background-color: red;
}
```
&nbsp;

#### mcc-player-content-wrapper
Adjusts the properties of the stream view after the listener clicked on the initial button. The class can be used to change the dimensions of the stream view as well.
```
mycrocast-floating-button-player::part(mcc-player-content-wrapper) {  
    background-color: red;
}
```
&nbsp;

#### mcc-play-pause-controls
Changes the properties of the play/pause-button within the stream view. Affects both the icon and the text besides it.
```
mycrocast-floating-button-player::part(mcc-play-pause-controls) {  
    color: black;  
}
```
&nbsp;

#### mcc-stop-listen-button
Changes the property of the stop-listen-button within the stream view. Affects both the icon and the text besides it.
```
mycrocast-floating-button-player::part(mcc-stop-listen-button) {  
    color: black;  
}
```
&nbsp;

#### mcc-delay-menu-button
Changes the properties of the delay-menu-button within the stream view. Affects both the icon and the text besides it.
```
mycrocast-floating-button-player::part(mcc-delay-menu-button) {  
    color: black;  
}
```
&nbsp;

#### mcc-next-stream-button
Changes the properties of the next-stream-button within the stream view. Affects both the icon and the text besides it.
```
mycrocast-floating-button-player::part(mcc-next-stream-button) {  
    color: black;  
}
```
&nbsp;

#### mcc-spot-item
Changes the properties of the spot title and the text "to be continued shortly" when a spot is being played.
```
mycrocast-floating-button-player::part(mcc-spot-item) {  
    color: black;  
}
```
&nbsp;

#### mcc-player-content-close
Changes the properties of the close icon on the top right of the stream view.
```
mycrocast-floating-button-player::part(mcc-player-content-close) {  
    color: black;  
}
```
&nbsp;

#### mcc-message-info
The listener is occasionally shown status messages while listening, e.g. when the streamer is muted. The class customizes this status message.
```
mycrocast-floating-button-player::part(mcc-message-info) {  
    color: white;  
    background: blue;  
}
```
&nbsp;

#### mcc-message-danger
Displayed if there is a problem with the transmission. Behaves like mcc-message-info.
```
mycrocast-floating-button-player::part(mcc-message-danger) {  
    color: black;  
    background: darkred;  
}
```
&nbsp;

#### mcc-delay-current
Adjusts properties of the element displaying the current delay in seconds besides the delay bar.
```
mycrocast-floating-button-player::part(mcc-delay-current) {  
    color: deepskyblue;  
}
```
&nbsp;

#### mcc-delay-rewind-1s
Adjusts the button that increases the delay by one second. For the other buttons that set the delay, the classes are ```mcc-delay-rewind-5s```, ```mcc-delay-rewind-30s```, ```mcc-delay-forward-5s```, ```mcc-delay-forward-1s```, where "rewind" stands for increasing and "forward" for decreasing the delay.

Example for one of the buttons:
```
mycrocast-floating-button-player::part(mcc-delay-rewind-1s) {  
    color: black;  
}
```
&nbsp;

#### mcc-delay-to-live

Adjusts the button with the text "Live", which resets the delay to 0. To adjust the color, the variable ```--color``` must be set here!

Example:
```
mycrocast-floating-button-player::part(mcc-delay-to-live) {
    --color: black;
}
```


#### mcc-delay-bar-wrapper

Affects the delay bar in the delay menu as a whole. Can be used to define the background color and margins/paddings to other elements

Example:
```
mycrocast-floating-button-player::part(mcc-delay-bar-wrapper) {
    background-color: white;
    margin-left: 3em;
}
```
&nbsp;

#### mcc-delay-bar-buffered

Adjusts the indicator in the delay bar that shows how much audio data is currently buffered. Behaves similarly to mcc-delay-bar-wrapper
&nbsp;

#### mcc-delay-bar-current
Adjusts the indicator in the delay bar that shows how long the current delay is. Behaves similarly to mcc-delay-bar-wrapper
&nbsp;

## Full example with variables
The following code snippet shows an example HTML page that embeds the player and adjusts its properties using CSS variables:

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

        mycrocast-lite-player {
            --mcc-player-background-color: #555555;  
            --mcc-player-font-color: #ff2e2e;
  
            --mcc-player-delay-bar-background: #bb2222;  
            --mcc-player-delay-bar-buffer: #ff2e2e;  
            --mcc-player-delay-bar-current: #ff8888;
        }
    </style>
</body>
</html>
```

### Result:

![image](https://github.com/mycrocast/webplayer-documentation/assets/82024455/4c4ce992-4dea-48cd-a9e5-03f810e9ff33)

&nbsp;

## Full example with parts


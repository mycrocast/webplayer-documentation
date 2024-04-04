# Mycrocast Webplayer Documentation

This document serves as a guide on how to embed the various webplayer types of mycrocast. We also provide some examples on how to customize the players for your organization's needs and in which ways you can do so.

# Table of contents
1. [Webplayer Lite](#lite-player)
2. [Floating-Button Webplayer](#floating)

# Webplayer Lite <a name="lite-player"></a>
## Embed Script

The following script needs to be copied and inserted anywhere within the ```<body>``` of your website.

```
<script
	id="mycrocast_base"
	src="https://mycrocast-webplayer.s3.eu-central-1.amazonaws.com/versioning-main.js" player=”LITE_PLAYER”>
</script>
```
  &nbsp;
  
## Embed Webplayer

The following HTML element is inserted where the player should be visible. The token attribute needs to be replaced with your club's token found in the mycrocast club admin platform.

```
<mycrocast-lite-player
	token="1567504890375_8741a554-c25e-428f-a807-a69bac373315-9999">
</mycrocast-lite-player>
```
&nbsp;

## Adjust Player Elements
You can make adjustments to parts of the webplayer using CSS. The styles can be added via a ```<style>``` tag in the ```<body>```, or via an external stylesheet that is imported in the ```<head>```.

### Adjustment of colors using CSS variables

CSS variables can only be used to adjust the colors of the web player. Standard CSS colors, but also hexadecimal codes and RGBA colors can be used as colors. The following variables are defined:

|Variable|Explanation|
|----|----|
| mcc-player-background-color | Adjusts the background color of the entire player. |
| mcc-player-font-color | Adjusts the font color of the player, including all icons. |
| mcc-player-overlay-color | Adjusts the background color of the delay menu. |
| mcc-player-overlay-font-color | Changes the font color within the delay menu, including all buttons for setting the delay. |
| mcc-player-button-disabled-color | Some buttons can be deactivated sometimes. By default, the color is set to grey, which can be changed using this variable. |
| mcc-player-delay-bar-background | Adjusts the background color of the delay bar in the delay menu |
| mcc-player-delay-bar-buffer | Adjusts the color of the indicator in the delay bar that shows the currently buffered audio data. Also affects the color of the "Live" button if no delay is set. |
| mcc-player-delay-bar-current | Adjusts the color of the indicator in the delay bar that represents the currently set delay. |

The CSS style of the website should embed the variables similar to the following example:

```
mycrocast-lite-player {
    --mcc-player-background-color: red;
    --mcc-player-font-color: white;
	
    --mcc-player-overlay-color: #000000af;
    --mcc-player-overlay-font-color: white; 
	
    --mcc-player-button-disabled-color: gray;
	
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
mcc-lite-player::part(mcc-lite-player-viewport) {
    /* define custom styles here */
}
```
  
Here, "mcc-lite-player-viewport" can be replaced by one of the class names defined on the following pages in order to customize various elements. The examples focus primarily on adjusting the colors, but any other CSS properties such as ```margin```, ```padding```, ```display```, ```position```, etc. can be defined for each class as required. Icons are interpreted as characters and can therefore be customized via ```font-size```, ```color```, etc.
&nbsp;

#### mcc-lite-player-viewport

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

![](https://github.com/mycrocast/webplayer-documentation/assets/82024455/c09ac585-654e-4be0-adaf-d0a9ddadf76f)
&nbsp;

#### mcc-play-pause-controls

Affects the play/pause icon on the left-hand side of the player. 

Example:

```
mcc-lite-player::part(mcc-play-pause-controls) {
    color: #ff2e2e;
    padding: 0 2em;
}
```

Result:

![](https://github.com/mycrocast/webplayer-documentation/assets/82024455/bab0154a-d44b-4e1a-b155-766279a51a4c)

&nbsp;
#### mcc-play-pause-controls-disabled

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

![](https://github.com/mycrocast/webplayer-documentation/assets/82024455/d212d2d0-a686-4759-9a73-39a80782c7fe)
&nbsp;

#### mcc-stream-title

Adjusts the properties of the stream title shown besides the play/pause-button.

Example:

```
mcc-lite-player::part(mcc-stream-title) {
    color: #ff2e2e;
}
```

Result:

![image](https://github.com/mycrocast/webplayer-documentation/assets/82024455/f8a65bff-4313-4091-a132-58985432f688)
&nbsp;

#### mcc-listener-info

Adjusts the properties of the element containing the number of listeners. Affects both the icon and the displayed number. Can also be hidden with display: none if required.

Example:
```
mcc-lite-player::part(mcc-listener-info) {
    color: #ff2e2e;
 
    /*optional: can be hidden using the following code*/
    display: none;
}
```

Result (not hiding the element):

![image](https://github.com/mycrocast/webplayer-documentation/assets/82024455/fa353145-f98b-4f00-819f-c9806106a799)
&nbsp;

#### mcc-stream-info

Adjusts the properties of the other stream information (language and the stream start time).

Example:
```
mcc-lite-player::part(mcc-stream-info) {
    color: #ff2e2e;
}
```

Result:

![image](https://github.com/mycrocast/webplayer-documentation/assets/82024455/985e0ecf-c5fc-4a14-b199-d302407addae)
&nbsp;

#### mcc-delay-overlay-button

Affects the icon on the right-hand side of the player that opens the synchronization menu.

Example:

```
mcc-lite-player::part(mcc-delay-overlay-button) {
    color: #ff2e2e;
}
```

Result:

![image](https://github.com/mycrocast/webplayer-documentation/assets/82024455/c1a8c938-83f9-436e-9f89-26c6268da37a)
&nbsp;

#### mcc-delay-overlay-button-disabled

Just like the play/pause button, the button for opening the delay menu is disabled in certain scenarios as well. The classes are exchanged here too, which is why all the properties set in mcc-delay-overlay-button must be adopted in mcc-delay-overlay-button-disabled. Only the color should also be changed here to give the listener visual feedback that the button is disabled.

Example:
```
mcc-lite-player::part(mcc-delay-overlay-button-disabled) {
    color: #bb2222;
}
```

Result:

![image](https://github.com/mycrocast/webplayer-documentation/assets/82024455/86fb1786-b9fa-4a23-99e6-067195b98696)
&nbsp;

#### mcc-spot-item

When an advertisement is played, some elements in the player disappear and the user is shown the text "Advertisement - to be continued shortly". mcc-spot-item affects the element that contains this text.

Example:
```
mycrocast-lite-player::part(mcc-spot-item) {
    color: deepskyblue;
}
```

&nbsp;
#### mcc-message-info

The listener is occasionally shown status messages while listening, e.g. when the streamer is muted. The class customizes this status message.

Example:
```
mycrocast-lite-player::part(mcc-message-info) {
    color: white;
    background-color: deepskyblue;
}
```
  
Result:

![](https://lh7-us.googleusercontent.com/c10c8HDRZgPFeXE9QykDl58vh4EcScDz9lctBqm4aU4UhXxb_vN6BfPLomUMIyOvn2xafWmwgBzsMt4e1EhsR17h594JIw2e7i_T-MnRpOU1V2gL6-HpTojcWdEO6EJB_qLBA3eqBM2jTN3D_P-JklM)

&nbsp;
#### mcc-message-danger

Displayed if there is a problem with the transmission. Behaves like mcc-message-info.

Example:
```
mycrocast-lite-player::part(mcc-message-danger) {
    color: white;
    background-color: darkred;
}
```

Result:

![](https://lh7-us.googleusercontent.com/hLhHK-64-1ssqLKbvyLEjtw17zNiWjtCMweAObgyIE1WDF-jf2Gnl3UKwd27ea49rgyo521abNci7TzmIwLgBroxv49LI3G_u3-tPC6ozTepYFpdpd6R1YPYUxho2FnQxCGzD8_-fGotdFvuRj2tO84)

&nbsp;
#### mcc-stream-placeholder

Customizes to the element that is displayed when no transmission is available.

Example:
```
mycrocast-lite-player::part(mcc-stream-placeholder) {
    color: deepskyblue;
}
```

Result:

![](https://lh7-us.googleusercontent.com/oe16ms40X1DKJotyx6ke6gUrbqOAv_B_e6juKTzcW3XJa5vnrniHWPx92WLwFIy39ClkGM1b1valCEv-tsLHobXE3qC9UR3VkTV6-GDCKnGNDTEE8JSvQm6x8Hc4s-iU17mj85XTbCHb3uD75HaLfS8)

&nbsp;
#### mcc-next-stream

If several streams are available, a button is displayed at the bottom of the player which the listener can use to navigate between different streams.

Example:
```
mycrocast-lite-player::part(mcc-next-stream) {
    color: white;
}
```

Result:

![](https://lh7-us.googleusercontent.com/UHY_T9c8c9lpmo8MiHc2OUw30bsyJY1ZVNlsaJP6x8xf_AoQ-4CwXtFh32nJpGRunW3uhtFUv_Ze8d4wG0ie7AyoAR3r7-Lf-KpRFvCQt_k8mptrGFgDJ6HWCkFzb09n5fMM7zGyVzZDAfZZJN0oeNw)

&nbsp;
#### mcc-delay-overlay-wrapper

Can be used to set the color, padding, and other properties of the delay overlay

Example:
```
mycrocast-lite-player::part(mcc-delay-overlay-wrapper) {
    background-color: #000000af;
}
```

Result:

![](https://lh7-us.googleusercontent.com/CSqfpqi9fSJkOPoJZiX9SwsCVzcxcvzQoyZYmfHLN0ESIT0yY9Bd0OyqN5-zXQjjRXAJqzyTlcKasy-4qO1LZiBhlMYPbA1nME5JgZILzBgBcHJIXwoljZ4d7S-3cFTQbAtXS5i-vkXzURVTFlYkuKA)

&nbsp;
#### mcc-delay-play-pause-controls

As the delay menu can have a different color, the play/pause button can also be different here. Can be customized like mcc-play-pause-controls.

&nbsp;
#### mcc-delay-play-pause-controls-disabled

The play/pause button can be deactivated in the delay menu as well. Again, all properties of mcc-delay-play-pause-controls should be adopted and only the color should be adjusted as visual indication.

&nbsp;
#### mcc-delay-current

Adjusts the element containing the current delay in seconds in the delay menu.

Example:
```
mycrocast-lite-player::part(mcc-delay-current) {
    color: deepskyblue;
}
```

Result:

![](https://lh7-us.googleusercontent.com/-xSmAiUNKt0ySmkAhNyZi2vPGz_RtIGOhUlaNMwvzbObJamklo3lirXajznCA1XpHo2Dc78an9TSRfo1cFN9c9avwfpNu4-yQM8_c0M_0IzEfSYdGC-KPbQiiJXDnSqudGJgp6ZR20XkRcsbat8YuMw)

&nbsp;
#### mcc-delay-overlay-close

Adjusts the button that closes the delay menu.

Example:
```
mycrocast-lite-player::part(mcc-delay-overlay-close) {
    color: deepskyblue;
}
```

Result:

![](https://lh7-us.googleusercontent.com/iNzMMGawzDCuGviG3hS482id_HYFgxF_ffnuM0dESpiKcBnB-02N69Ajq8JYRJ8N46mXuEALsoKygNVRZAU6f3tsK5HagFhPgL6jcMNfWfOjyZveD8HZstVBfjDCCJGJHv_U5pz0thAedZ3kjmZjFl8)

&nbsp;
#### mcc-delay-rewind-1s

Adjusts the button that increases the delay by one second. For the other buttons that set the delay, the classes are ```mcc-delay-rewind-5s```, ```mcc-delay-rewind-30s```, ```mcc-delay-forward-5s```, ```mcc-delay-forward-1s```, where "rewind" stands for increasing and "forward" for decreasing the delay.

Example for one of the buttons:
```
mycrocast-lite-player::part(mcc-delay-rewind-1s) {
    color: deepskyblue;
}
``` 

Result:

![](https://lh7-us.googleusercontent.com/dr42XWMVfS_LH2DEEd0s4huLbLu8HIRfOCq4v9Bj6XOUND89wFbc0eoMKO6qe0anHKeosM5mr9BO4C1-5H8TaRueGKSCpXvAgpackVlLXgsDafDsWz8WLTCVp2sZLLVLB2zD0zgTGPje_Oziu_Drr7Q)

&nbsp;
#### mcc-delay-to-live

Adjusts the button with the text "Live", which resets the delay to 0. To adjust the color, the variable ```--color``` must be set here!

Example:
```
mycrocast-lite-player::part(mcc-delay-to-live) {
    --color: deepskyblue;
}
```

Result:

![](https://lh7-us.googleusercontent.com/qFuyPSj3zbCfFdw_Xrx6q4EfmFbZ6cw556NMRehAfPZ51vZLZx3FLmLTAo3EQCcJr6-ZBSeZaMhFVeBLkX-ZGS5tcck8Nyrdv7dxXXMc9hKFDFY1JcKrYAThaEyPHlnI-fxKhzlsSYzk0L7GwwgThsQ)

&nbsp;
#### mcc-delay-bar-wrapper

Affects the delay bar in the delay menu as a whole. Can be used to define the background color and margins/paddings to other elements

Example:
```
mycrocast-lite-player::part(mcc-delay-bar-wrapper) {
    background-color: white;
    margin-left: 3em;
}
```

Result:

![](https://lh7-us.googleusercontent.com/9P691gmUBVmRomZsFnjM3vmf5BIaTY0RBMH9dDxbabehgK2JZVp3rOXtNPabgRzz7xSUQKACf20xI0pG9Y5MSkMz4RusOFXATwvAN4GEJUnOtOffC6ILvAndqSnbdv8MwZMIzDLD1kZIWS55lnXsH8U)

&nbsp;
#### mcc-delay-bar-buffered

Adjusts the indicator in the delay bar that shows how much audio data is currently buffered. Behaves similarly to mcc-delay-bar-wrapper

&nbsp;
#### mcc-delay-bar-current

Adjusts the indicator in the delay bar that shows how long the current delay is. Behaves similarly to mcc-delay-bar-wrapper

# Floating-Button Webplayer <a name="floating"></a>
&nbsp;
## Embed Script

The following script needs to be copied and inserted anywhere within the ```<body>``` of your website.

```
<script
	id="mycrocast_base"
	src="https://mycrocast-webplayer.s3.eu-central-1.amazonaws.com/versioning-main.js"
	player=”FLOATING_BUTTON_PLAYER”>
</script>
```
&nbsp;

## Embed Webplayer

The following HTML element is inserted where the player should be visible. The token attribute needs to be replaced with your club's token found in the mycrocast club admin platform.

```
<mycrocast-lite-player
	token="1567504890375_8741a554-c25e-428f-a807-a69bac373315-9999">
</mycrocast-lite-player>
```
&nbsp;

## Adjust Player Elements
You can make adjustments to parts of the webplayer using CSS. The styles can be added via a ```<style>``` tag in the ```<body>```, or via an external stylesheet that is imported in the ```<head>```.

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

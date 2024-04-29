# Visual-Impaired Webplayer

## Adjust Player Elements
You can make adjustments to parts of the webplayer using CSS. The styles can be added via a ```<style>``` tag in the ```<body>```, or via an external stylesheet that is imported in the ```<head>```. Adjustments are made by setting CSS variables or by modifying shadow DOM parts. You can find fully implemented examples for both at the end of this page.

### Adjustment of colors using CSS variables

CSS variables can only be used to adjust the colors of the web player. Standard CSS colors, but also hexadecimal codes and RGBA colors can be used as colors. The following variables are defined:

|Variable|Explanation|
|----|----|
| mcc-player-background-color | Adjusts the background color of the button and the content view. |
| mcc-player-header-color | Adjusts the background color of the webplayer header which contains the mycrocast logo. This is the one and only option to change the header's appearance, since we do NOT provide a shadow part below.|
| mcc-player-font-color | Adjusts the font color of the player, including all icons. Also sets the color of the border of the content view. |
| mcc-player-stream-background | Adjusts the background color of the stream items. |
| mcc-player-overlay-color | Adjusts the background color of the advertisement overlay. The overlay is a little transparent by default. |
| mcc-player-overlay-font-color | Adjusts the font color within the advertisement overlay. |
| mcc-player-highlight-color | Adjusts the highlighting color of the active stream. |

The CSS style of the website should embed the variables similar to the following example:

```
mycrocast-floating-button-player {  
    --mcc-player-background-color: #555555;  
    --mcc-player-header-color: #555555;  
    --mcc-player-font-color: #ff2000;  
  
    --mcc-player-stream-background: black;  
  
    --mcc-player-overlay-color: #ff2000;  
    --mcc-player-overlay-font-color: black;  
    --mcc-player-highlight-color: #ff2000;
}
```  

Not all variables need to be defined.

&nbsp;

### Adjustments to other properties

A CSS class or a CSS shadow part can be overwritten as follows:

```
mycrocast-vi-button-player::part(mcc-vi-player-viewport) {
    /* define custom styles here */
}
```
  
Here, ```mcc-vi-player-viewport``` can be replaced by one of the class names defined below in order to customize various elements. The examples focus primarily on adjusting the colors, but any other CSS properties such as ```margin```, ```padding```, ```display```, ```position```, ```width```, etc. can be defined for each class as required. Icons are interpreted as characters and can therefore be customized via ```font-size```, ```color```, etc.

### mcc-vi-player-viewport
Can be used to adjust the height, width and shape of the player. Also can be used to set the background color of the header by setting the ```background-color``` property

Example:
```
mycrocast-vi-player::part(mcc-vi-player-viewport) {  
    background-color: #555555;
    width: 600px;
    border-radius: 1em;
}
```

Result:

### mcc-stream-container
Can be used to adjust the container which contains the available streams.

Example:
```
mycrocast-vi-player::part(mcc-stream-container) {
    background-color: #555555;
}
```

Result:


### mcc-stream-placeholder
Can be used to adjust the text that is shown when no stream is available.

```
mycrocast-vi-player::part(mcc-stream-placeholder) {
    color: #ff2000;
}
```

### mcc-stream-item
Can be used to adjust the properties of the stream items as a whole.

Example:

```
mycrocast-vi-player::part(mcc-stream-item) {
    background-color: #ff2000;
}
```

In case you want to adjust the behavior of the stream highlighting, you can add the ```active``` and ```hover``` pseudo-classes to the shadow part.

Example:

```

```

Result:


### mcc-stream-title
Adjusts the properties of the stream title within the stream items.

Example:

```
mycrocast-vi-player::part(mcc-stream-title) {
    color: white;
}
```



Result:


### mcc-stream-language
Adjusts the properties of the stream language within the stream items.
```
mycrocast-vi-player::part(mcc-stream-language) {
    color: white;
}
```

Result:


### mcc-play-pause-controls
Adjusts the properties of the play, pause and loading button within the stream item. The size of the icons can be adjusted with the ```--icon-size``` variable.
```
mycrocast-vi-player::part(mcc-play-pause-controls) {
    --icon-size: 1em
    color: white;
}
```

Result:

### mcc-icon-play
When adjusting the ```--icon-size``` variable in ```mcc-play-pause-controls```, it may occur that the play icon does not seem to be in the middle of the button anymore. This class can be used to fine-tune the properties of this specific icon.

Example:
```
mycrocast-vi-player::part(mcc-message-info) {
    color: ff2000;
	background-color: white;
}
```

### mcc-message-info
The listener is occasionally shown status messages while listening, e.g. when the streamer is muted. The class customizes these status messages.
```
mycrocast-vi-player::part(mcc-message-info) {
    color: ff2000;
	background-color: white;
}
```

Result:


### mcc-message-danger
Displayed if there is a problem with the transmission. Behaves like mcc-message-info.
```
mycrocast-vi-player::part(mcc-message-danger) {
    background-color: darkred;
	color: white;
}
```

Result:

### mcc-spot-overlay-wrapper
When an advertisement is played during the stream, an overlay appears over the stream items, showing the remaining time of the advertisement break. This class can be used to adjust the properties of the overlay.

```
mycrocast-vi-player::part(mcc-spot-overlay-wrapper) {
    background-color: #ff2000;
}
```

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


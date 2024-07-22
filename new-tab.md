# New-Tab-Button Webplayer

## Adjust Player Elements
You can make adjustments to parts of the webplayer using CSS. The styles can be added via a ```<style>``` tag in the ```<body>```, or via an external stylesheet that is imported in the ```<head>```. Adjustments are made by setting CSS variables or by modifying shadow DOM parts. You can find fully implemented examples for both at the end of this page.

### Adjustment of colors using CSS variables

CSS variables can only be used to adjust the colors of the web player. Standard CSS colors, but also hexadecimal codes and RGBA colors can be used as colors. The following variables are defined:

|Variable|Explanation|
|----|----|
| mcc-player-background-color | Adjusts the background color of the button and the content view. |

The CSS style of the website should embed the variables similar to the following example:

```
mycrocast-floating-button-tab-player {
    --mcc-player-background-color: #555555;  
}
```  

Not all variables need to be defined.

&nbsp;

### Adjustments to other properties

A CSS class or a CSS shadow part can be overwritten as follows:

```
mycrocast-floating-button-tab-player::part(mcc-player-initial-button) {
    /* define custom styles here */
}
```
  
Here, ```mcc-player-initial-button``` can be replaced by one of the class names defined on the following pages in order to customize various elements. The examples focus primarily on adjusting the colors, but any other CSS properties such as ```margin```, ```padding```, ```display```, ```position```, ```width```, etc. can be defined for each class as required. Icons are interpreted as characters and can therefore be customized via ```font-size```, ```color```, etc.

### mcc-player-initial-button
Adjusts the properties of the button shown initially when a stream is available. The class can be used to change its size as well.

Example:
```
mycrocast-floating-button-tab-player::part(mcc-player-initial-button) {  
    background-color: #555555;
    width: 5em;
    height: 5em;
    border: 2px solid #ff2000;
}
```

Result:

![image](https://github.com/mycrocast/webplayer-documentation/assets/82024455/b977504c-eff1-46d1-a651-e4347f33ff8a)
&nbsp;

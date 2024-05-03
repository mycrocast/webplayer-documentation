# Visually-Impaired Webplayer

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
mycrocast-vi-player {
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

![image](https://github.com/mycrocast/webplayer-documentation/assets/82024455/233871a3-0753-43cf-9994-e57784894375)

&nbsp;

### mcc-stream-container
Can be used to adjust the container which contains the available streams.

Example:
```
mycrocast-vi-player::part(mcc-stream-container) {
    background-color: #ff2000;
    padding: 2em;
}
```

Result:

![image](https://github.com/mycrocast/webplayer-documentation/assets/82024455/3dc1e31d-460d-4df1-b798-7391c6c3eec5)

&nbsp;

### mcc-stream-placeholder
Can be used to adjust the text that is shown when no stream is available.

Example:

```
mycrocast-vi-player::part(mcc-stream-placeholder) {
    color: #ff2000;
}
```

Result:

![image](https://github.com/mycrocast/webplayer-documentation/assets/82024455/87fc4013-bbe9-4a9b-9b12-336e664e312b)

&nbsp;

### mcc-stream-item
Can be used to adjust the properties of the stream items as a whole.

Example:

```
mycrocast-vi-player::part(mcc-stream-item) {
    background-color: #ff2000;
}
```

Result:

![image](https://github.com/mycrocast/webplayer-documentation/assets/82024455/9da34d88-ff50-4bae-b7f1-dac343ce2ab4)

In case you want to adjust the behavior of the stream highlighting, you can add the ```hover``` pseudo-class to the shadow part as follows:

Example:

```
mycrocast-vi-player::part(mcc-stream-item):hover {
    transition: 0.5s ease;
    box-shadow: 0px 0px 10px 10px white;
}
```

Result when hovering a stream:

![image](https://github.com/mycrocast/webplayer-documentation/assets/82024455/5b5c6430-cd9d-416a-8df3-e767dbb5dc59)

&nbsp;

### mcc-stream-title
Adjusts the properties of the stream title within the stream items.

Example:

```
mycrocast-vi-player::part(mcc-stream-title) {
    color: #ff2000;
}
```

Result:

![image](https://github.com/mycrocast/webplayer-documentation/assets/82024455/a0a7222c-e1dd-43fd-9a19-7c8173171442)

&nbsp;

### mcc-stream-language
Adjusts the properties of the stream language within the stream items.
```
mycrocast-vi-player::part(mcc-stream-language) {
    color: #ff2000;
}
```

Result:

![image](https://github.com/mycrocast/webplayer-documentation/assets/82024455/31160241-3be8-408b-b629-f3ef770f9c35)

&nbsp;

### mcc-play-pause-controls
Adjusts the properties of the play, pause and loading button within the stream item. The size of the icons can be adjusted with the ```--icon-size``` variable.
```
mycrocast-vi-player::part(mcc-play-pause-controls) {
    --icon-size: 1em
    color: #ff2000;
    box-shadow: 0px 0px 10px 6.5px #ff2000;
}
```

Result:

![image](https://github.com/mycrocast/webplayer-documentation/assets/82024455/ec3ec5bc-3533-492d-8cda-8eee3c3b32b4)

&nbsp;

### mcc-icon-play
When adjusting the ```--icon-size``` variable in ```mcc-play-pause-controls```, it may occur that the play icon does not seem to be in the middle of the button anymore. This class can be used to fine-tune the properties of this specific icon.

Example:
```
mycrocast-vi-player::part(mcc-icon-play) {
    padding-left: 7px
}
```

Result:

![image](https://github.com/mycrocast/webplayer-documentation/assets/82024455/e0172361-817b-4372-a23d-5db8564b6890)

&nbsp;

### mcc-message-info
The listener is occasionally shown status messages while listening on the top of the player, e.g. when the streamer is muted. The class customizes these status messages.
```
mycrocast-vi-player::part(mcc-message-info) {
    color: ff2000;
    background-color: white;
}
```

Result:

![image](https://github.com/mycrocast/webplayer-documentation/assets/82024455/a93c46e7-fcd6-4c11-bf6c-be1fb259956c)

&nbsp;

### mcc-message-danger
Displayed if there is a problem with the transmission. Behaves like mcc-message-info.
```
mycrocast-vi-player::part(mcc-message-danger) {
    background-color: darkred;
    color: white;
}
```

Result:

![image](https://github.com/mycrocast/webplayer-documentation/assets/82024455/736a43cf-da6e-4c62-b56b-6c78cc970e89)

&nbsp;

### mcc-spot-overlay-wrapper
When an advertisement is played during the stream, an overlay appears over the stream items, showing the remaining time of the advertisement break. This class can be used to adjust the properties of the overlay.

```
mycrocast-vi-player::part(mcc-spot-overlay-wrapper) {
    background-color: #ff2000;
}
```

Result:

![image](https://github.com/mycrocast/webplayer-documentation/assets/82024455/1d2edd76-c93c-4fe2-acd5-227e1cd2a8c7)

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
    <script id="mycrocast_base" src="https://mycrocast-webplayer.s3.eu-central-1.amazonaws.com/versioning-main.js" player=VISUAL_IMPAIRED_PLAYER></script>
    <style>
        mycrocast-vi-player {
            --mcc-player-background-color: #555555;  
            --mcc-player-header-color: #555555;  
            --mcc-player-font-color: #ff2000;  
    
            --mcc-player-stream-background: black;  
    
            --mcc-player-overlay-color: #ff2000;  
            --mcc-player-overlay-font-color: black;  
            --mcc-player-highlight-color: #ff2000;  
        }
    </style>
</body>
</html>
```

### Resulting player

![image](https://github.com/mycrocast/webplayer-documentation/assets/82024455/a7574b10-f96c-4363-b06a-20ad6508050c)

![image](https://github.com/mycrocast/webplayer-documentation/assets/82024455/3e5b0bba-dffc-4bd4-bfbe-a891aa01dd42)



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
        mycrocast-vi-player::part(mcc-vi-player-viewport) {  
            background-color: #555555;  
            width: 600px;  
            border-radius: 1em;  
        }  
  
        mycrocast-vi-player::part(mcc-stream-container) {  
            background-color: #ff2000;  
            padding: 2em;  
        }  
  
        mycrocast-vi-player::part(mcc-stream-placeholder) {  
            color: #ff2000;  
        }  
  
        mycrocast-vi-player::part(mcc-stream-item) {  
            background-color: #ff2000;  
        }  
  
        mycrocast-vi-player::part(mcc-stream-item):hover {  
            transition: 0.5s ease;  
            box-shadow: 0px 0px 10px 10px white;  
        }  
  
        mycrocast-vi-player::part(mcc-stream-title) {  
            color: #ff2000;  
        }  
  
        mycrocast-vi-player::part(mcc-stream-language) {  
            color: #ff2000;  
        }  
  
        mycrocast-vi-player::part(mcc-play-pause-controls) {  
            --icon-size: 1.5em;  
            color: #ff2000;  
            box-shadow: 0px 0px 10px 6.5px #ff2000;  
        }  
  
        mycrocast-vi-player::part(mcc-icon-play) {  
            padding-left: 7px;  
        }  
  
        mycrocast-vi-player::part(mcc-message-info) {  
            background-color: white;  
            color: #f20000;  
        }  
  
        mycrocast-vi-player::part(mcc-message-danger) {  
            background-color: darkred;  
            color: white;  
        }  
  
        mycrocast-vi-player::part(mcc-spot-overlay-wrapper) {  
            background-color: #ff2000;  
        }
    </style>
</body>
</html>
```

### Resulting player

![image](https://github.com/mycrocast/webplayer-documentation/assets/82024455/cec0fb1f-445e-4ca1-b926-1427c76871ff)

![image](https://github.com/mycrocast/webplayer-documentation/assets/82024455/6b376eb7-f40f-4201-a761-1fe704c50ea9)

![image](https://github.com/mycrocast/webplayer-documentation/assets/82024455/d33ecea4-4c1d-4fa2-9b34-cf5bf3f26b9d)

![image](https://github.com/mycrocast/webplayer-documentation/assets/82024455/3773dcbc-9a9a-4a85-a8fb-c7a4a4c4fde3)

![image](https://github.com/mycrocast/webplayer-documentation/assets/82024455/2479f312-df61-4098-baa3-8fa4831942f2)





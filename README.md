# Mycrocast Webplayer Documentation

This document serves as a guide on how to embed the various webplayer types of mycrocast. We also provide some examples on how to customize the players for your organization's needs and in which ways you can do so.

# Table of contents
1. [Webplayer Lite](https://mycrocast.github.io/webplayer-documentation/player/lite)
2. [Floating-Button Webplayer](https://mycrocast.github.io/webplayer-documentation/player/floating)

# General

## Choose your player

We provide three different players you can choose from.

### Webplayer Lite

// TODO add image

### Webplayer Floating-Button
//TODO
### Visual-Impaired Webplayer
//TODO
## Embed Script

The following script needs to be copied and inserted anywhere within the ```<body>``` of your website. Please replace the ```LITE_PLAYER``` tag in the ```player="LITE_PLAYER"``` attribute with the tag according to your player from the list below.

```
<script
	id="mycrocast_base"
	src="https://mycrocast-webplayer.s3.eu-central-1.amazonaws.com/versioning-main.js"
	player=”LITE_PLAYER”>
</script>
```
&nbsp;

| Webplayer type | Tag |
|-----|-----|
| Webplayer Lite | LITE_PLAYER |
| Webplayer Floating-Button | FLOATING_BUTTON_PLAYER |
| Visual-Impaired Webplayer | VISUAL_IMPAIRED_PLAYER |

## Embed Webplayer

The following HTML snippets show what the player tags need to look like. They need to be inserted where the player should be visible. The token in the ```token="1567504890375_8741a554-c25e-428f-a807-a69bac373315-9999"``` attribute needs to be replaced with your club's token found in the mycrocast club admin platform.

&nbsp;

#### Webplayer-Lite
```
<mycrocast-lite-player
	token="1567504890375_8741a554-c25e-428f-a807-a69bac373315-9999">
</mycrocast-lite-player>
```
&nbsp;

#### Webplayer Floating-Button
```
<mycrocast-floating-button-player
    token="1567504890375_8741a554-c25e-428f-a807-a69bac373315-9999">
</mycrocast-floating-button-player>
```
&nbsp;

#### Visual-Impaired Webplayer
```
<mycrocast-vi-player
    token="1567504890375_8741a554-c25e-428f-a807-a69bac373315-9999">
</mycrocast-vi-player>
```
&nbsp;

### Obtaining the club token from the mycrocast platform

1. Log in with your club account.
2. Navigate to the Settings->Webplayer tab on the left.
3. On the top, select the "SDK" tab.
4. The club token is on the right-hand side of the view. Click on the eye-icon to copy it to your clipboard.
5. Go back to your player and replace the mycrocast token with your copied club's token.

## Customizing your webplayer
We provide means to customize the webplayer to your needs. Since the elements and classes are very specific to each player, we describe them individually on their own pages.

1. [Webplayer Lite](https://mycrocast.github.io/webplayer-documentation/player/lite)
2. [Floating-Button Webplayer](https://mycrocast.github.io/webplayer-documentation/player/floating)



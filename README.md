# Mycrocast Webplayer Documentation

This document serves as a guide on how to embed the various webplayer types of mycrocast. We also provide some examples on how to customize the players for your organization's needs and in which ways you can do so.

# General

## Choose your player

We provide three different players you can choose from.

### Webplayer Lite

![image](https://github.com/mycrocast/webplayer-documentation/assets/82024455/f5157569-2d69-4f74-89ee-d921b4b8d17d)
&nbsp;

### Visually-Impaired Webplayer

![image](https://github.com/mycrocast/webplayer-documentation/assets/82024455/06ed7946-6b95-415f-b3d5-b1a382c3b9e1)
&nbsp;

### Webplayer Floating-Button

The Floating-Button webplayer has a fixed position on the screen. It is only shown when there is an active stream, and hidden if there is not.

![image](https://github.com/mycrocast/webplayer-documentation/assets/82024455/a1469b08-ccec-4c3d-8e8b-98520c400dd8)
&nbsp;

### New-Tab Webplayer

The New-Tab webplayer has a fixed position on the screen. Just like the Floating-Button webplayer, it is only shown when there is an active stream. However, when clicking on the initial button, it opens another webplayer in a new tab.

![image](https://github.com/user-attachments/assets/1f55de9d-e5dd-4f16-91bb-ff3aff1c19af)
&nbsp;

### Webplayer Sticky-Footer

The Sticky-Footer webplayer has a fixed position on the screen. Just like the Floating-Button webplayer, it is only shown when there is an active stream. However, the initial button also contains the stream title here, and when clicking on it, it opens the following stream view at the bottom of the page.

![image](https://github.com/user-attachments/assets/afe0a279-f3dc-4d40-9557-c866c397db05)

&nbsp;

## Embed Script

The following script needs to be copied and inserted anywhere within the ```<body>``` of your website. Please replace the ```LITE_PLAYER``` tag in the ```player=LITE_PLAYER``` attribute with the tag according to your player from the list below.

```
<script
	id="mycrocast_base"
	src="https://mycrocast-webplayer.s3.eu-central-1.amazonaws.com/versioning-main.js"
	player=LITE_PLAYER>
</script>
```
&nbsp;

| Webplayer type | Tag |
|-----|-----|
| Webplayer Lite | LITE_PLAYER |
| Webplayer Floating-Button | FLOATING_BUTTON_PLAYER |
| Visually-Impaired Webplayer | VISUAL_IMPAIRED_PLAYER |
| New-Tab Webplayer | FLOATING_BUTTON_TAB_PLAYER |
| Sticky-Footer Webplayer | STICKY_FOOTER_PLAYER |

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

#### Visually-Impaired Webplayer
```
<mycrocast-vi-player
    token="1567504890375_8741a554-c25e-428f-a807-a69bac373315-9999">
</mycrocast-vi-player>
```
&nbsp;

#### Webplayer Floating-Button
```
<mycrocast-floating-button-player
    token="1567504890375_8741a554-c25e-428f-a807-a69bac373315-9999">
</mycrocast-floating-button-player>
```
&nbsp;

#### New-Tab Webplayer
```
<mycrocast-floating-button-tab-player
    token="1567504890375_8741a554-c25e-428f-a807-a69bac373315-9999">
</mycrocast-floating-button-tab-player>
```
&nbsp;

#### Webplayer Sticky-Footer
```
<mycrocast-sticky-footer-player
    token="1567504890375_8741a554-c25e-428f-a807-a69bac373315-9999">
</mycrocast-sticky-footer-player>
```
&nbsp;

### Obtaining the club token from the mycrocast platform

1. Log in with your club account.
2. Navigate to the Settings->Webplayer tab on the left.
   ![image](https://github.com/mycrocast/webplayer-documentation/assets/82024455/0c2bec14-54ff-4a1d-8518-dab3ba545850)

3. On the top, select the "SDK" tab.
   ![image](https://github.com/mycrocast/webplayer-documentation/assets/82024455/daaf54a1-09de-439c-9552-6d0ee1412bc3)

4. The club token is on the right-hand side of the view. Click on the copy button to copy it to your clipboard.
   ![image](https://github.com/mycrocast/webplayer-documentation/assets/82024455/4fb73e5d-d241-40aa-b3d6-ba797ee4a0e5)

5. Go back to your player and replace the mycrocast token with your copied club's token.

## Customizing your webplayer
We provide means to customize the webplayer to your needs. Since the elements and classes are very specific to each player, we describe them individually on their own pages.

1. [Webplayer Lite](https://mycrocast.github.io/webplayer-documentation/lite)
2. [Floating-Button Webplayer](https://mycrocast.github.io/webplayer-documentation/floating)
3. [Visually-Impaired Webplayer](https://mycrocast.github.io/webplayer-documentation/vi)
4. [New-Tab Webplayer](https://mycrocast.github.io/webplayer-documentation/new-tab)
5. [Sticky-Footer Webplayer](https://mycrocast.github.io/webplayer-documentation/sticky-footer)



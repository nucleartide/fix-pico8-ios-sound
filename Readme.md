# fix-pico8-ios-sound

Fix sound when playing PICO-8 games on iOS

## Motivation

[PICO-8](https://www.lexaloffle.com/pico-8.php) is a game creation tool that allows you to export your game as JavaScript for browser play. While this works beautifully on desktop browsers, it doesn't work as well on iOS Safari, where sound doesn't work.\* This is a darn shame, because playing a PICO-8 game on iOS is otherwise extremely slick – try [pico8_html_template](https://github.com/headjump/pico8_html_template) on an iPhone for a demonstration.

It turns out that sound doesn't work because iOS mutes Web Audio until the user interacts with the page. As a workaround, [Paul Bakaus](https://paulbakaus.com/tutorials/html5/web-audio-on-ios/) recommends adding a "tap to play" button to your game. The script provided by this repo demonstrates how to do so. You should use the script as a starting point for your own "tap to play" customization.

\* _I don't own any Android devices, so I can't say anything about Android._

## Install

Download the script to the same directory as your game's exported HTML and JavaScript file.

```bash
curl https://raw.githubusercontent.com/nucleartide/fix-pico8-ios-sound/master/fix-pico8-ios-sound.js --output fix-pico8-ios-sound.js
```

(You can also visit the link, right-click, and save.)

Then, in your exported HTML file, locate the `<script>` tag that refers to your JavaScript file. For example, if your JavaScript file is named `cart.js`, you should look for the following:

```html
<script async type="text/javascript" src="cart.js"></script>
```

Delete that line, and add a reference to `fix-pico8-ios-sound.js`:

```html
<script src="fix-pico8-ios-sound.js" data-original-file="cart.js"></script>
```

Note that the `data-original-file` attribute is required. This attribute tells the script of the original file's path, so that it can be dynamically loaded.

Now, if you open your game's HTML file in iOS Safari, you will need to tap the screen before the game loads:

<p align="center">
  <a href="https://user-images.githubusercontent.com/914228/32412008-2c3fa8de-c1c1-11e7-816b-00301a209c11.jpeg">
    <img width="300" src="https://user-images.githubusercontent.com/914228/32412008-2c3fa8de-c1c1-11e7-816b-00301a209c11.jpeg">
  </a>
</p>

## Feedback, improvements, comments

Feel free to open an [issue](https://github.com/nucleartide/fix-pico8-ios-sound/issues/new)!

---

> <a href="https://user-images.githubusercontent.com/914228/32412070-c4ca8fa0-c1c2-11e7-93c7-e39e46c1fcb4.png">
>   <img width="100" src="https://user-images.githubusercontent.com/914228/32412070-c4ca8fa0-c1c2-11e7-93c7-e39e46c1fcb4.png">
> </a>
>
> GitHub [@nucleartide](https://github.com/nucleartide) · Twitter [@nucleartide](https://twitter.com/nucleartide)

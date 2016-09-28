# Waiter

The front-end code increases monumentally day-by-day. In enterprise apps, I see vendor JavaScript files spikes to MBs even after compression. Loading these huge files gives a very unpleasant experience for the end-user because they've to just stare the blank white screen for a while! Sometimes it's just difficult to cut down the size and in those cases it's better to provide a nice welcome screen to release the tension of the user.
 
Waiter is a simple pre-loading screen built with pure JS and CSS3. It don't have any dependency with 3rd party libraries. Waiter provides option to display your logo image with a nice fake progressbar that gives an illusion the page is loading soon!
 
Please check the [demo](http://prideparrot.com/demos/waiter/demo1.html)!

## How to use

Just 3 steps!

1) Move your application stylesheets and scripts to the end of &lt;body&gt;. Note, for the stylesheets you should specify `property` attribute as `stylesheet` to pass the HTML5 validation ([Ref](http://stackoverflow.com/a/22195559/741616)).

```html
...    
    <link rel="stylesheet" property="stylesheet" href="app.min.css" >
    <script src="app.min.js"></script>
</body>
```

2) Copy everything from *waiter.css* and drop it inline with &lt;style&gt; element under &lt;head&gt;.

```html
<style>
    [content from waiter.css]
</style>
```

3) Copy everything from *waiter.js* and drop it inline with &lt;script&gt; element and it should be the first child of the &lt;body&gt;.

```html
<body>
    <script>
        [content from waiter.js]
    </script>
    [...other content]
</body>
```

Don't reference the files by `href` or `src` and that beats the purpose of Waiter! You can further improve the experience by compression.

## Options and Customization 

`manual` - boolean, defaults to `false`. When supplied `true`, removing the waiter has to be manually called by `window.waitOver()`.

You can pass this option as an attribute in the &lt;script&gt; tag.

```html
<script data-manual="true">[...]</script>
```

You can change the base64 logo image and customize the background color of the waiter and progress bar by modifying the below variables in *waiter.scss* file. You can convert SCSS to CSS online from [here](http://beautifytools.com/scss-compiler.php).

`$logo` - base64 string of the logo image. You can create base64 string of your JPG, PNG logo image online using this [tool](https://www.base64-image.de/).

`$bgColor` - Waiter background color

`$progressBarColor` - Progress bar color

### Changing Animation

As default when the wait is over the waiter slides up. You can change the animation by overriding the `anime` and `trigger` CSS classes.

Below are couple of different animations you could try.

#### Fade 
[demo](http://prideparrot.com/demos/waiter/demo2.html)

```css
&.anime {
    transition: opacity 0.5s;
    
    &.trigger {
        opacity: 0;
    }
}
```

#### Vapour
[demo](http://prideparrot.com/demos/waiter/demo3.html)

```css
&.anime {
    transition: all .5s ease-in-out;
    
    &.trigger {
        transform: scale(2);
        opacity: 0;
    }
}
```

If you are not happy with the above animations you can roll your own :)
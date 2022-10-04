# 1.4 - Navigating with pat-inject and pat-navigation

Documentation: https://patternslib.com/demos/inject#documentation

You can also use `pat-inject` for ajax based navigation without doing full page reloads.
In this example we use it together with `pat-navigation`, which can mark a navigation item with current or in-path classes based on the URL of the page or where you just clicked at.

To make a good example, we need to move away from this pat-markdown / pat-inject based tutorial because we want to see if the navigation is correctly highlighted as promised whenwe directly visit a URL.

In this example, we have the following structure:


```html
<!DOCTYPE html>
<html>
  <head>
    <meta charset="UTF-8" />
    <title>inject/navigation demo</title>
    <script src="http://localhost:3001/bundle.min.js"></script>
    <link rel="stylesheet" href="./styles.css" />
  </head>
  <body>
    <div class="container">

      <a
          href="./navigation.html"
          class="pat-inject"
          data-pat-inject="
              target: self::element;
              trigger: autoload
      ">load navigation</a>

      <div id="content">
        <h1>start page</h1>
      </div>

    </div>
  </body>
</html>
```


We have a `pat-inject` statement which loads the seperate navigation structure automatically (`trigger: autoload`) and replaces itself with the contents (`target: self::element` and implicitly `source: body`, which is the default).
There is also the `#content` area where the pages are injected into.

If JavaScript is turned off you can still navigate around - can go to the navigation and to the individual linked pages and use the browser's back button to go back where you have been before.

All the pages have the same structure, so that you can directly go to them via using their URL. In a real world example you would have some framework, so that you don't have t repeat the page structure boilerplate for each page over and over again.

The navigation strucuture looks like this:


```html
<!DOCTYPE html>
<html>
  <head>
    <meta charset="UTF-8" />
    <title>navigation</title>
  </head>
  <body>
    <nav
        class="pat-navigation"
        data-pat-inject="
            source: #content;
            target: #content;
            history: record;
    ">
      <ul>
        <li>
          <a href="./start.html" class="pat-inject">Start</a>
        </li>
        <li>
          <a href="./page1.html" class="pat-inject">Page 1</a>
          <ul>
            <li>
              <a href="./page1.1.html" class="pat-inject">Page 1.1</a>
            </li>
          </ul>
        </li>
        <li>
          <a href="./page2.html" class="pat-inject">Page 2</a>
        </li>
      </ul>
    </nav>
  </body>
</html>
```


On the `<nav>` element the `pat-navigation` pattern is initialized.
When navigating around it will mark the navigation items with the configurable but here default classes `.current` and `.navigation-in-path`.
Try to open one of the items in a new tab. The JavaScript should add the correct classes to the navigation items and a in-path link should be shown in green and the current link in red.
Please note: Google Chrome seems to strip away the `.html` file extension. Setting the navigation classes based on URL comparison would not work in that case.

These are the relevant CSS definitions:


```css
.container {
    display: flex;
}

.current {
    color: red;
}
```


The `<nav>` element also defines some common settings for `pat-navigation`.
Apart from `source` and `target` the `history: record` is interesting.
It makes sure that the current ULR is updated in the history object and that the URL is shown in the browser's URL bar.

Now go to the demo and try it out: <a href="/1.04/start.html">./start.html</a>


# 1.1 Integrating Patternslib, Basics and pat-toggle

pat-toggle Documentation: https://patternslib.com/demos/toggle#documentation


## Basic Integration

To use Patternslib, just add the Patternslib script to your website and start using it's classes on DOM nodes.

There are several ways to integrate the Patternslib script.

### Use a CDN

The Patternslib bundle is added to the npm package and and can be directly loaded from a CDN.

Here is an example with the jsDelivr service:

```html
<!DOCTYPE html>
<html>
  <head>
    <meta charset="UTF-8" />
    <title>Patternslib training</title>
    <script src="https://cdn.jsdelivr.net/npm/@patternslib/patternslib@9.9.4/dist/bundle.min.js"></script>
  </head>
  ...
```

And one with UNPKG:

```html
<!DOCTYPE html>
<html>
  <head>
    <meta charset="UTF-8" />
    <title>Patternslib training</title>
    <script src="https://unpkg.com/@patternslib/patternslib@9.9.4/dist/bundle.min.js"></script>
  </head>
  ...
```

### Download the bundle

The latest bundle can be found on the [GitHub releases page](https://github.com/Patternslib/Patterns/releases).
Unter "Assets" you can find a zip file named `patternslib-bundle-X.Y.Z.zip`.

A bundle can also be found at the [Patternslib download site](https://patternslib.com/download).


### Build your own bundle

You can also build your own bundle by cloning the [Patternslib repository](https://github.com/Patternslib/Patterns) from GitHub and following the [README instructions](https://github.com/Patternslib/Patterns/blob/master/README.md).

This offers the greatest flexibility but is an expert option.

You can extend the Patternslib repository, include exactly the patterns you want to include and include your own patterns.

As an example, look at the [Mockup repository](https://github.com/plone/mockup/) or at [pat-leaflet](https://github.com/patternslib/pat-leaflet).


## Basic configuration

You might want to disable modernizr, which is automatically loaded from the base Patternslib bundle.
There is also an useful option to automatically include depending CSS styles from 3rd party addons.
This config must be loaded before the Patternslib bundle.

```html
<!DOCTYPE html>
<html>
  <head>
    <meta charset="UTF-8" />
    <title>Patternslib training</title>
    <script>
      window.__patternslib_disable_modernizr = true;
      window.__patternslib_import_styles = true;
    </script>
    <script src="https://cdn.jsdelivr.net/npm/@patternslib/patternslib@9.9.4/dist/bundle.min.js"></script>
  </head>
  ...
```


## Integrate more bundles

Since the integration of the Webpack Module Federation feature you can directly integrate other patterns without loading shared resoruces like jQuery twice.
For more information visit the Patternslib documentaion on [Webpack Module Federation](https://github.com/Patternslib/Patterns/blob/master/docs/developer/module-federation.md).

To integrate another bundle, you can add the bundle's remote.min.js file.
This is an example integrating pat-leaflet:

```html
<!DOCTYPE html>
<html>
  <head>
    <meta charset="UTF-8" />
    <title>Patternslib training</title>
    <script>
      window.__patternslib_disable_modernizr = true;
      window.__patternslib_import_styles = true;
    </script>
    <script src="https://cdn.jsdelivr.net/npm/@patternslib/patternslib@9.9.4/dist/bundle.min.js"></script>
    <script src="https://cdn.jsdelivr.net/npm/@patternslib/pat-leaflet@2.1.1/dist/remote.min.js"></script>
  </head>
  ...
```



### Example Integration


```html
<!DOCTYPE html>
<html>
  <head>
    <meta charset="UTF-8" />
    <title>Integrating Patternslib</title>
    <script>
      window.__patternslib_disable_modernizr = true;
      window.__patternslib_import_styles = true;
    </script>
    <script src="https://cdn.jsdelivr.net/npm/@patternslib/patternslib@9.9.4/dist/bundle.min.js"></script>
  </head>
  <body>

    <button
        class="pat-toggle"
        data-pat-toggle="selector: body; value: dark bright; store: session"
    >
        Change theme
    </button>

    <style>
      body.dark {
        background: #333;
        color: #FFF;
      }
    </style>

  </body>
</html>

```

Demo:

<button
    class="pat-toggle"
    data-pat-toggle="
      selector: body;
      value: dark bright;
      store: session">
  Change theme
</button>

<style>
  body.dark {
    background: #333;
    color: #FFF;
  }
</style>


## Pattern configuration

Patterns are configured via data attributes and in some cases by extra classes.
In the example above, the configuration is done via the ``data-pat-toggle`` attribute.

The configuration syntax is inspired by the CSS syntax.
Boolean values are supported but avoided, as they also do not exist in CSS.
Everything should be as simple as possible.

The configuration is also aquired from parent elements.
Consider the following example:


<div class="pat-clone-code">
<div data-pat-toggle="selector: button.pat-toggle">
  <button class="pat-toggle" data-pat-toggle="value: bg-red default">Toggle button background</button>
  <button class="pat-toggle" data-pat-toggle="value: fg-blue default">Toggle button color</button>
  <style>
    .bg-red { background-color: red; }
    .fg-blue { color: blue; }
  </style>
</div>
</div>


## pat-toggle accordion example

Patternslib helps you out where CSS isn't enough.
That's at least the basic idea - but there are also bigger Patterns which provide rich UIs for different purposes like text editors or mapping libraries.

Let's see how the toggle pattern can help us to create a simple accordion:


<div class="pat-clone-code">
<div>
  <button class="pat-toggle" data-pat-toggle="selector: #example-1-1--accordion; value: opened closed">Show/hide the accordion</button>
  <section id="example-1-1--accordion" class="closed">
    <img src="https://picsum.photos/400/600" alt="random image from the internet" />
  </section>
  <style>
    .closed {
      height: 0;
      overflow: hidden;
      transition: height 1s;
    }
    .opened {
      height: 600px;
      overflow: hidden;
      transition: height 1s
    }
  </style>
</div>
</div>


## Toggle attributes

While we're already at the toggle pattern, let's finish it up.

We can also toggle attributes with pat-toggle.

Let's show/hide an element via the ``hidden`` attribute.


<div class="pat-clone-code">
<div>
  <button class="pat-toggle" data-pat-toggle="selector: #example-1-1--show-hide; attribute: hidden">Show/hide the element</button>
  <section id="example-1-1--show-hide" hidden>
    <img src="https://picsum.photos/400/600" alt="random image from the internet" />
  </section>
</div>
</div>


## Patternslib documentation

You can find more information on the individual Patterns of Patternslib at: https://patternslib.com/

For example, the toggle Pattern is documented here: https://patternslib.com/demos/toggle

The Patternslib repository can be found here: https://github.com/patternslib/patterns


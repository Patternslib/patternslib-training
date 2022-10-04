# 1.1 Integrating Patternslib, Basics and pat-toggle

pat-toggle Documentation: https://patternslib.com/demos/toggle#documentation


## Basic Integration

To use Patternslib, just add the Patternslib script to your website and start using it's classes on DOM nodes.

```html
<!DOCTYPE html>
<html>
  <head>
    <meta charset="UTF-8" />
    <title>Integrating Patternslib</title>
    <script src="http://localhost:3001/bundle.min.js"></script>
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

<div
  class="pat-clone"
  data-pat-clone="
    trigger-behaviour: auto;
    clone-behaviour: escape;
    clone-wrapper: #code-template;
  ">
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


<div
  class="pat-clone"
  data-pat-clone="
    trigger-behaviour: auto;
    clone-behaviour: escape;
    clone-wrapper: #code-template;
  ">
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


<div
  class="pat-clone"
  data-pat-clone="
    trigger-behaviour: auto;
    clone-behaviour: escape;
    clone-wrapper: #code-template;
  ">
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


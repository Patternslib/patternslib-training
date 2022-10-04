# 1.3 - pat-inject

Documentation: https://patternslib.com/demos/inject#documentation

With ``pat-inject`` you can load remote content with great variety.

Have a look at the [options reference](https://patternslib.com/demos/inject#optionsreference) on how to customize it and to the [modifiers reference](https://patternslib.com/demos/inject#modifiers) on how to use special pseudo-element like keywords for further customizing the ``source`` and ``target`` arguments.

``pat-inject`` only works on anchor elements, forms and as a special case on a [``.pat-subform``](https://patternslib.com/demos/subform) element.


## A simple example

This example just loads remote text from a html file next to this one.

<div class="pat-clone-code">
<div>
  <a href="/1.03/inject-text.html"
      class="pat-inject"
      data-pat-inject="source: #text; target: #target-1">Load remote text</a>
  <div id="target-1">Injected content will appear here.</div>
</div>
</div>


## Loading markdown, reinitializing patterns.

Another example - load some markdown content from the previous pat-switch example.
You can see that any patterns in the remotely loaded content are also initialized.

<div class="pat-clone-code">
<div>
  <a href="/1.02/index.md"
      class="pat-inject"
      data-pat-inject="target: #target-2">Load pat-switch tutorial</a>
  <div id="target-2">Injected content will appear here.</div>
</div>
</div>


## Automatically in-view loading

``pat-inject`` can also load automatically when the ``pat-inject`` element comes into view via the ``trigger: autoload-visible`` parameter.

First, let's define an space which moves the demo out of view for sure.
When you scroll down a mp3 player should appear.

<strong>scroll down....</strong>

<div>
  <div style="height: 100vh"></div>
</div>

Now, let's initialize.

We use the special argument ``features: load-inline-script`` here.
This loads scripts defined in the external file.
For security reasons, this is not enabled by default.

TODO: check above statement, coordinate if we can leave ``load-inline-script`` in ``pat-inject``.

<div class="pat-clone-code">
<div>
  <a href="/1.03/wavesurfer.html"
      class="pat-inject"
      data-pat-inject="
        trigger: autoload-visible;
        source: body;
        target: self::element;
        features: load-inline-script">Load wavesurfer.js demo</a>
</div>
</div>


## A like button with pat-inject enabled forms

pat-inject on forms turn them into ajax based forms the values are submitted via ajax.

A simple example is a like button.

The beauty in this example is also that a form is used. This is semantically just correct. Data is changed on the server side, so a form fits much better than a simple link.

<div class="pat-clone-code">
<form
    action="/1.03/inject-like.html"
    class="pat-inject"
    data-pat-inject="target: self::element">
  <button
      type="submit"
      name="like_button"
      value="like"
      class="pat-tooltip"
      data-pat-tooltip="trigger: hover; position-list: tm">Like
    <sup class="counter">(3)</sup>
  </button>
</form>
</div>


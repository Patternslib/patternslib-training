# 1.3 - pat-inject

Documentation: https://patternslib.com/demos/inject#documentation

With ``pat-inject`` you can load remote content with great variety.

Have a look at the [options reference](https://patternslib.com/demos/inject#optionsreference) on how to customize it and to the [modifiers reference](https://patternslib.com/demos/inject#modifiers) on how to use special pseudo-element like keywords for further customizing the ``source`` and ``target`` arguments.

``pat-inject`` only works on anchor elements, forms and as a special case on a [``.pat-subform``](https://patternslib.com/demos/subform) element.


## A simple example

This example just loads remote text from a html file next to this one.

<div
  class="pat-clone"
  data-pat-clone="
    trigger-behaviour: auto;
    clone-behaviour: escape;
    clone-wrapper: #code-template;
  ">
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

<div
  class="pat-clone"
  data-pat-clone="
    trigger-behaviour: auto;
    clone-behaviour: escape;
    clone-wrapper: #code-template;
  ">
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

<div
  class="pat-clone"
  data-pat-clone="
    trigger-behaviour: auto;
    clone-behaviour: escape;
    clone-wrapper: #code-template;
  ">
  <div>
    <div style="height: 100vh"></div>
  </div>
</div>

Now, let's initialize.

We use the special argument ``features: load-inline-script`` here.
This loads scripts defined in the external file.
For security reasons, this is not enabled by default.

TODO: check above statement, coordinate if we can leave ``load-inline-script`` in ``pat-inject``.

<div
  class="pat-clone"
  data-pat-clone="
    trigger-behaviour: auto;
    clone-behaviour: escape;
    clone-wrapper: #code-template;
  ">
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

# Adding and removing classes with pat-switch.

Documentation: https://patternslib.com/demos/switch#documentation

pat-switch can be used to add or remove classes from an element.

<div
  class="pat-clone"
  data-pat-clone="
    trigger-behaviour: auto;
    clone-behaviour: escape;
    clone-wrapper: #code-template;
  ">
<div id="pat-switch-anchor">
  <a href="#pat-switch-anchor"
      class="pat-switch"
      data-pat-switch="selector: body; remove: font-*; add: font-small;">Small text</a>
  <a href="#pat-switch-anchor"
      class="pat-switch"
      data-pat-switch="selector: body; remove: font-*;">Normal text</a>
  <a href="#pat-switch-anchor"
      class="pat-switch"
      data-pat-switch="selector: body; remove: font-*; add: font-large;">Large text</a>
  <style>
    .font-small { font-size: 0.8em; }
    .font-large { font-size: 1.2em; }
  </style>
</div>
</div>


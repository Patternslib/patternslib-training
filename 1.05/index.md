# 1.5 - Datagrid-like forms with pat-clone, pat-sortable, pat-validation and pat-inject

There are a variety of patterns which helps you with forms.
Let's look at three of those.

We already saw how `pat-inject` changes a form so that POST or GET requests are sent via ajax and the page is not reloaded.

`pat-clone` can be used to build a datagrid-like field.
Basically it clones a markup structure and appends it just to the end of the `pat-clone`'s contents.
Form names and ids are incremented, you can define a maximum number of clones and have a button to delete individual clones.

Together with `pat-sortable` You can even reoder the individual clones.

And then there is `pat-validation` which hooks into the validation API with some extra constraints like a `before` and `after` date constraints.
`pat-validation` displays the system's default translated warning messages for standard form constraints or configurable messages for custom constraints.
Since it's built upon the browser's validation API you can also use the `:invalid` or `:valid` pseudo CSS selectors.

Now, lets look at a example and some code:


<div class="pat-clone-code">
<form
    action="./1.05/submitted.html"
    class="pat-inject pat-validation"
    data-pat-inject="target: self::element">
  <fieldset
      class="pat-clone pat-sortable"
      data-pat-clone="
          template: #clone-template;
          trigger-element: .clone-trigger;
          max: 5"
      data-pat-sortable="
          selector: fieldset.clone
      ">
  </fieldset>
  <div>
    <!-- Clone trigger -->
    <button
        type="button"
        class="clone-trigger">
      Add new session.
    </button>
    <button
        class="pat-button"
        type="submit">
      Submit
    </button>
  </div>
  <template id="clone-template">
    <fieldset class="clone">
      <legend>Training session #{1}</legend>
      <input
          name="title-#{1}"
          size="20"
          max="20"
          placeholder="Training title"
          required
          />
      <input
          class="pat-date-picker"
          name="start-#{1}"
          type="date"
          placeholder="start"
          data-pat-validation="not-after: [name=end-#{1}]"
          data-pat-date-picker="output-format: MMMM Do YYYY"
          />
      <input
          class="pat-date-picker"
          name="end-#{1}"
          type="date"
          placeholder="end"
          data-pat-validation="not-before: [name=start-#{1}]"
          data-pat-date-picker="output-format: MMMM Do YYYY"
          />
      <button
          class="remove-clone"
          type="button">Remove
      </button>
    </fieldset>
  </template>
</form>
</div>


Let's add some extra styles:

<div class="pat-clone-code">
<style>
  time.output-field {
    min-width: 6em;
    height: 1em;
    padding: 0.25em;
    background: lightgrey;
    display: inline-block;
  }
  [required] {
    border: 1px solid red;
  }
  input:invalid {
    background-color: LightSalmon;
  }
  .warning {
    border: 1px solid DarkOrange;
    background: Beige;
  }
  time .cancel-button::after {
    display: inline-block;
    content: " 🚫 ";
  }
  .placeholder {
    color: grey;
    font-size: 0.8em;
  }
</style>
</div>



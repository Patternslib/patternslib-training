# 1.5 - Forms with pat-inject, pat-clone and pat-validation

<div class="pat-clone-code">
<form action="." class="pat-inject pat-validation">
    <fieldset>
        <fieldset
            class="pat-clone"
            data-pat-clone="
                template: #clone-template;
                trigger-element: .clone-trigger;
                max: 5">
            <fieldset class="clone">
                <legend>Family member 1</legend>
                <input
                    name="name-1"
                    size="20"
                    placeholder="Name"
                    required
                />
                <input
                    class="pat-date-picker"
                    name="date-1"
                    type="date"
                    placeholder="birthdate"
                />
                <button
                    class="remove-clone"
                    type="button">Remove
                </button>
            </fieldset>
        </fieldset>
        <div>
            <!-- Clone trigger -->
            <button
                type="button"
                class="clone-trigger">
                Add an extra family member
            </button>
            <button
                class="pat-button"
                type="submit">
                submit
            </button>
        </div>
    </fieldset>
</form>
<template id="clone-template">
  <fieldset>
    <legend>Family member #{1}</legend>
    <input
        name="name-#{1}"
        size="20"
        placeholder="Name"
        required
    />
    <input
        class="pat-date-picker"
        name="date-#{1}"
        type="date"
        placeholder="birthdate"
    />
    <button
        class="remove-clone"
        type="button">Remove
    </button>
  </fieldset>
</template>
</div>



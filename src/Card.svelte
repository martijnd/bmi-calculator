<script>
  import { createEventDispatcher } from "svelte";

  export let title;
  export let unit;

  let value;

  const dispatch = createEventDispatcher();

  const update = event => {
    dispatch("update", { title, value: event.target.value });
  };
</script>

<div
  class="Card mt-10 p-4 relative bg-primary-dark max-w-xs mx-auto rounded-lg">
  <label
    class="text-center text-primary text-3xl font-bold uppercase"
    for={title}>
    {title}
  </label>
  <input
    id={title}
    class="mx-auto border-none bg-transparent w-full text-10xl text-white
    font-bold text-center"
    type="number"
    bind:value
    on:input={update}
    step="1"
    placeholder="..."
    min="1" />
  <span
    class="absolute text-primary text-6xl -right-6px bottom-0 uppercase
    font-bold"
    style="line-height: 0.7;">
    {unit}
  </span>
</div>

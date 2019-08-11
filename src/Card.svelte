<script>
  import { createEventDispatcher } from "svelte";

  export let title;
  export let unit;

  const dispatch = createEventDispatcher();

  const update = event => {
    console.log(event);
    dispatch("update", { title, data: event.data });
  };
</script>

<div class="Card bg-primary-dark mt-4 max-w-xs mx-auto rounded-lg p-4">
  <h2 class="text-center text-primary text-3xl font-bold uppercase">{title}</h2>
  <input
    class="border-none bg-transparent mx-auto w-full text-6xl text-white
    text-center"
    type="number"
    on:input={update}
    step="1"
    min="1" />
  <span class="absolute">{unit}</span>
</div>

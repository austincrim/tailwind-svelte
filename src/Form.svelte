<script>
  export let addHandler;
  let newTitle = "";
</script>

<input
  autocomplete="off"
  bind:value={newTitle}
  class="rounded h-8"
  type="text" />
<button
  on:click={() => {
    addHandler({ title: newTitle, done: false });
    newTitle = '';
  }}
  class="py-1 px-6 text-white font-semibold rounded bg-indigo-500
  hover:bg-indigo-600">
  Add item
</button>

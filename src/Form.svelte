<script>
  export let addHandler;
  let newTitle = "";
</script>

<style>
  button:active {
    @apply bg-indigo-700;
  }
</style>

<div class="text-left">
  <label class="font-semibold mb-2" for="newItem">New Item</label>
  <input
    id="newItem"
    autocomplete="off"
    bind:value={newTitle}
    class="rounded h-8 mr-2"
    type="text" />
  <button
    on:click={() => {
      addHandler({ title: newTitle, done: false });
      newTitle = '';
    }}
    class="py-1 px-6 text-white font-semibold rounded bg-indigo-500
    hover:bg-indigo-400">
    Add item
  </button>
</div>
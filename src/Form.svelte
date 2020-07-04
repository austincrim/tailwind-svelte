<script>
    import uid from "uid";
    export let addHandler;
    let newTitle = "";
</script>

<style>
    button:active {
        @apply bg-orange-700;
    }
</style>

<div class="text-left">
    <label class="font-semibold mb-2" for="newItem">New Item</label>
    <!-- svelte-ignore a11y-autofocus -->
    <input
        id="newItem"
        autocomplete="off"
        bind:value={newTitle}
        on:keydown={(e) => {
            if (e.key === 'Enter') {
                addHandler({ title: newTitle, done: false, id: uid() });
                newTitle = '';
            }
        }}
        class="p-1 rounded h-8 mr-2"
        autofocus
        type="text" />
    <button
        on:click={() => {
            addHandler({ title: newTitle, done: false, id: uid() });
            newTitle = '';
        }}
        class="py-1 px-6 text-white font-semibold rounded bg-orange-400
        hover:bg-orange-500">
        Add item
    </button>
</div>

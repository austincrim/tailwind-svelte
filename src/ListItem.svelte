<script>
  export let todo;
  export let removeHandler, checkHandler;
</script>

<style>
  button {
    transition: transform 0.1s ease-in;
  }

  button:hover {
    transform: translateY(-2px);
  }

  button:active {
    transform: translateY(1px);
  }

  .done {
    text-decoration: line-through;
    opacity: 0.5;
  }
</style>

<li
  class="flex justify-between mb-4 px-4 py-3 font-semibold bg-gray-200 rounded
  border-b-2 border-blue-600 shadow">
  <div class:done="{todo.done}">{todo.title}</div>

  <div>
    <button
      on:click={() => checkHandler(todo)}
      class="border-none rounded px-1 ml-3">
      &#10004;
    </button>
    <button
      on:click={() => removeHandler(todo.id)}
      class="border-none rounded px-1 ml-1">
      &#10006;
    </button>
  </div>
</li>

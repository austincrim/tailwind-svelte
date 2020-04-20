<script>
  import Tailwindcss from "./Tailwindcss.svelte";
  import ListItem from "./ListItem.svelte";
  import Form from "./Form.svelte";

  let items = [
    {
      title: "Get groceries",
      done: false
    },
    {
      title: "Do laundry",
      done: false
    },
    {
      title: "Finish homework",
      done: false
    }
  ];

    function sortArray(a, b) {        
        if(a.done) return 1;
        if(b.done) return -1;
        return 0;
        
    }

  function addTodo(newTodo) {
    if (newTodo.title) {
      items = [...items, newTodo];
    }
  }

  function removeTodo(title) {
    items = items.filter(item => item.title != title);
  }

  function checkTodo(todo) {
    items[items.indexOf(todo)] = { title: todo.title, done: !todo.done };
  }
</script>

<main>
  <Tailwindcss />
  <div class="flex text-gray-700 font-sans justify-evenly">
    <div class="mt-2">
      <ul>
        {#each items.sort(sortArray) as item}
          <ListItem
            checkHandler={checkTodo}
            removeHandler={removeTodo}
            todo={item} />
        {/each}
      </ul>
    </div>

    <div class="text-center mt-2">
        <Form addHandler={addTodo}/>
    </div>
  </div>
</main>

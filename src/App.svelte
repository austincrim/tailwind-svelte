<script>
  import Tailwindcss from "./Tailwindcss.svelte";
  import ListItem from "./ListItem.svelte";
  import Form from "./Form.svelte";
  import Header from "./Header.svelte";
  import Progress from "./Progress.svelte";

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

  
  $: percentComplete = Math.floor((items.filter(i => i.done).length / items.length) * 100)

  function sortArray(a, b) {
    if (a.done) return 1;
    if (b.done) return -1;
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
    console.log(percentComplete);
  }

</script>

<style global>
  body {
    margin: 0;
    padding: 0;
  }
</style>

<main>
  <Tailwindcss />
  <Header />
<<<<<<< HEAD
  <Progress percentComplete={percentComplete} />
  <div class="flex text-gray-700 font-sans justify-evenly">
    <div class="mt-2">
=======
  <div class="flex flex-col-reverse md:flex-row max-w-full mx-auto text-gray-700 font-sans justify-evenly">
    <div class="mt-4 px-4 w-full">
>>>>>>> aaffb028ce07461c5b57eff483d3430a32c5c797
      <ul>
        {#each items.sort(sortArray) as item}
          <ListItem
            checkHandler={checkTodo}
            removeHandler={removeTodo}
            todo={item} />
        {/each}
      </ul>
    </div>

    <div class="text-center mt-4 w-full">
      <Form addHandler={addTodo} />
    </div>
  </div>
</main>

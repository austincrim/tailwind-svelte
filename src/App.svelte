<script>
  import Tailwindcss from './Tailwindcss.svelte';
  import ListItem from "./ListItem.svelte";
  import Form from "./Form.svelte";
  import Header from "./Header.svelte";
  import Progress from "./Progress.svelte";
  import uid from 'uid';

  let items = [
    {
      title: "Get groceries",
      done: false,
      id: uid()
    },
    {
      title: "Do laundry",
      done: false,
      id: uid()
    },
    {
      title: "Finish homework",
      done: false,
      id: uid()
    }
  ];

  $: percentComplete = Math.floor(
    (items.filter(i => i.done).length / items.length) * 100
  );

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

  function removeTodo(id) {
    items = items.filter(item => item.id != id);
  }

  function checkTodo(todo) {
    items[items.indexOf(todo)] = { title: todo.title, done: !todo.done };
    console.log(percentComplete);
  }
</script>

<style global>
  body {
    box-sizing: border-box;
    margin: 0;
    padding: 0;
  }
</style>

<main>
  <Tailwindcss />
  <Header />
  <Progress {percentComplete} />

  <div
    class="flex flex-col-reverse md:flex-row mx-auto p-8 text-gray-700 bg-gray-300 rounded shadow font-sans
    justify-evenly max-w-6xl">

    <div class="px-4 w-full">
      <ul>
        {#each items.sort(sortArray) as item}
          <ListItem
            checkHandler={checkTodo}
            removeHandler={removeTodo}
            todo={item} />
        {/each}
      </ul>
    </div>

    <div class="mb-4 px-4 w-full text-center md:text-left">
      <Form addHandler={addTodo} />
    </div>

  </div>
</main>

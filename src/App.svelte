<script>
    import Tailwindcss from "./Tailwindcss.svelte";
    import ListItem from "./ListItem.svelte";
    import Form from "./Form.svelte";
    import Header from "./Header.svelte";
    import Progress from "./Progress.svelte";
    import uid from "uid";

    let items = JSON.parse(window.localStorage.getItem("items"));

    if (!items || !items.length) {
        items = [
            {
                title: "Thanks for checking out my app!",
                done: false,
                id: uid(),
            }
        ];
        window.localStorage.setItem("items", JSON.stringify(items));
    }

    $: percentComplete =
        items.length === 0
            ? 0
            : Math.floor(
                  (items.filter((i) => i.done).length / items.length) * 100
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
        window.localStorage.setItem("items", JSON.stringify(items));
    }

    function removeTodo(id) {
        items = items.filter((item) => item.id != id);
        window.localStorage.setItem("items", JSON.stringify(items));
    }

    function checkTodo(todo) {
        items[items.indexOf(todo)] = {
            ...todo,
            title: todo.title,
            done: !todo.done,
        };
        window.localStorage.setItem("items", JSON.stringify(items));
    }
</script>

<style global>
    main {
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
        class="flex flex-col-reverse md:flex-row mx-auto p-8 text-gray-700
        bg-gray-300 rounded shadow font-sans justify-evenly max-w-6xl
        transition-all duration-200 ease-in-out">

        <div class="px-4 w-full">
            <ul>
                {#each items as item (item.id)}
                    <ListItem
                        checkHandler={checkTodo}
                        removeHandler={removeTodo}
                        todo={item} />
                {/each}
            </ul>
        </div>

        <div
            class="flex flex-col justify-start mb-4 px-4 w-full text-center
            md:text-left">
            <Form addHandler={addTodo} />
            <button
                class="py-1 px-6 mt-4 text-orange-800 font-semibold rounded
                bg-orange-200 border-none hover:bg-orange-300"
                on:click={() => (items = [...items.sort(sortArray)])}>
                Move Done to Bottom
            </button>
        </div>

    </div>
</main>

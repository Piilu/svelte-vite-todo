<script>
  let message = "";
  let items = [];

  function add() {
    if (message.trim() !== "") {
      items.push({ name: message, isDone: false });
      items = items;
    }
    message = "";
  }

  function keyDown(e) {
    if (e.key == "Enter") {
      add();
    }
  }
  $: doneItems = items.filter((x) => x.isDone == true);
  $: notDoneItems = items.filter((x) => x.isDone == false);
</script>

<main>
  <input on:keydown={(e) => keyDown(e)} type="text" bind:value={message} />
  <button on:click={add}>Add</button>
  <h1>All items</h1>
  <ul>
    {#each items as item}
      <li>{item.name} <input type="checkbox" bind:checked={item.isDone} /></li>
    {/each}
  </ul>

  <h1>Done items</h1>
  <ul>
    {#each doneItems as item}
      <li>{item.name} <input type="checkbox" bind:checked={item.isDone} /></li>
    {/each}
  </ul>

  <h1>Not done items</h1>
  <ul>
    {#each notDoneItems as item}
      <li>{item.name} <input type="checkbox" bind:checked={item.isDone} /></li>
    {/each}
  </ul>
</main>

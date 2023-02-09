<script>
  import ItemList from "./lib/ItemList.svelte";
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

<div class="container mx-auto m-3 flex justify-center items-center  flex-col">
  <div class="form-control">
    <div class="input-group">
      <input
        class="input input-bordered w-full max-w-xs"
        on:keydown={(e) => keyDown(e)}
        type="text"
        bind:value={message}
      />
      <button class="btn btn-square btn-primary" on:click={add}>Add</button>
    </div>
  </div>
  <ItemList title="All items" bind:items />
  <div class="divider" />
  <ItemList title="Done items" bind:items={doneItems} />
  <div class="divider" />
  <ItemList title="Not done items" bind:items={notDoneItems} />
</div>

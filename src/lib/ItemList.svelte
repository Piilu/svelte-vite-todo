<script>
  export let items;
  export let title;
</script>

<h1 class="font-xl font-bold">{title}</h1>
<ul class="list-disc">
  {#each items as item}
    <li>{item.name} <input class="checkbox checkbox-success" type="checkbox" bind:checked={item.isDone} /></li>
  {/each}
</ul>

<script>
  import Character from "./lib/Character.svelte";
  let character = [];
  let page = 1;
  async function loadCharacter() {
    const response = await fetch(
      "https://rickandmortyapi.com/api/character?page=" + page
    );
    const data = await response.json();
    character = data.results;
  }
  loadCharacter();

  function nextPage() {
    page++;
    loadCharacter();
  }
  function previosPage() {
    page--;
    loadCharacter();
  }
</script>

<h1 class="text-5xl text-center font-bold">Rick and Morty Svelte</h1>
<div class="max-w-screen-lg m-auto">
  <div class="btns pb-3">
    <button
      on:click={previosPage}
      disabled={page == 1 ? true : false}
      class="bg-gray-500 hover:bg-gray-700 text-white font-bold py-2 px-4 rounded"
      >Previos</button
    >
    <button
      on:click={nextPage}
      class="bg-gray-500 hover:bg-gray-700 text-white font-bold py-2 px-4 rounded"
      >Next</button
    >
  </div>
  <div class="grid grid-cols-4 gap-4">
    {#each character as { name, image }}
      <Character {name} {image} />
    {/each}
  </div>
</div>

<style>
  .btns{
    display: flex;
    justify-content: space-between;
  }
</style>

<script>
  export let name;
  export let image;
</script>

<div class="bg-neutral-700 text-center rounded-md" >
  <img class="rounded-lg shadow-lg" src={image} alt={name} />
  <h2 class="text-2xl font-bold text-white mb-2">{name}</h2>
</div>

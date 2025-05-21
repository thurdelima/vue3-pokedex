<script setup>
const pokemon = defineProps(['name', 'urlBaseSvg'])
</script>


<template>
  <div class="col-4">
    <div class="card p-2 mb-3 cardListPokemon">
      <p class="text-center">{{ pokemon.name }}</p>
      <img :src="urlBaseSvg" class="card-img-top" alt="..." height="80" />
    </div>
  </div>
</template>


<style scoped>
.cardListPokemon {
  background: rgb(72, 63, 251);
  background: radial-gradient(circle, rgba(94, 87, 232, 0.6) 0%, rgba(70, 252, 244, 0.2) 100%);
  cursor: pointer;
  box-shadow: rgba(0, 0, 0, 0.16) 0px 1px 4px;
}
.cardListPokemon:hover {
  background: rgb(72, 63, 251);
  background: radial-gradient(circle, rgba(72, 63, 251, 0.6) 0%, rgba(70, 252, 244, 0.4) 100%);
}
.cardListPokemon img:hover {
  padding: 0.1rem;
}
</style>
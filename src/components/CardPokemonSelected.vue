<script setup>
const pokemon = defineProps([
  'name',
  'xp',
  'height',
  'weight',
  'types',
  'abilities',
  'stats',
  'img',
  'loading',
])
</script>


<template>
  <div
    class="card CardPokemonSelected text-white"
    :class="loading ? '' : 'animate__animated animate__fadeInRight'"
  >
    <!-- <img :src="pokemon.img" class="card-img-top p-5" :alt="pokemon.name" /> -->

    <img v-if="pokemon.name" :src="pokemon.img" class="card-img-top pt-2" :alt="pokemon.name" />
    <img v-else src="../assets/egg_pokemon.svg" class="card-img-top pt-2" alt="???" />
    <div class="card-body">
      <h5 class="card-title text-center">{{ pokemon.name || '???' }}</h5>
      <hr />

      <div class="row text-center mb-3">
        <section class="col">
          <strong>XP:</strong>
          <span class="d-block">{{ pokemon.xp }}</span>
        </section>
        <section class="col">
          <strong>Height:</strong>
          <span class="d-block">{{ pokemon.height / 10 }} m</span>
        </section>
        <section class="col">
          <strong>Weight:</strong>
          <span class="d-block">{{ pokemon.weight / 10 }} kg</span>
        </section>
      </div>

      <div class="row">
        <div class="types mb-3 col" v-if="pokemon.types">
          <h6 class="text-center">Types</h6>
          <div class="d-flex justify-content-center gap-2">
            <span
              v-for="type in pokemon.types"
              :key="type.slot"
              class="badge rounded-pill type-badge"
              :class="'type-' + type.type.name"
            >
              {{ type.type.name }}
            </span>
          </div>
        </div>

        <div class="abilities mb-3 col" v-if="pokemon.abilities">
          <h6 class="text-center">Abilities</h6>
          <div class="d-flex flex-wrap justify-content-center gap-2">
            <span
              v-for="ability in pokemon.abilities"
              :key="ability.slot"
              class="badge rounded-pill ability-badge"
            >
              {{ ability.ability.name.replace('-', ' ') }}
            </span>
          </div>
        </div>
      </div>

      <div class="stats d-none d-sm-block" v-if="pokemon.stats">
        <h6 class="text-center mb-2">Stats</h6>
        <div class="stat-bar-container">
          <div v-for="stat in pokemon.stats" :key="stat.stat.name" class="stat-row mb-2">
            <div class="d-flex justify-content-between small">
              <span class="text-capitalize">{{ stat.stat.name.replace('-', ' ') }}:</span>
              <span>{{ stat.base_stat }}</span>
            </div>
            <div class="progress" style="height: 8px">
              <div
                class="progress-bar"
                role="progressbar"
                :style="{ width: (stat.base_stat / 255) * 100 + '%' }"
                :aria-valuenow="stat.base_stat"
                aria-valuemin="0"
                aria-valuemax="255"
              ></div>
            </div>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<style scoped>
.CardPokemonSelected {
  height: 75vh;
  background: #1f0dde;
  background: linear-gradient(
    90deg,
    rgba(31, 13, 222, 0.94) 0%,
    rgba(77, 77, 219, 0.91) 35%,
    rgba(179, 107, 242, 1) 100%
  );

  box-shadow: rgba(149, 157, 165, 0.2) 0px 8px 24px;
}
.CardPokemonSelected img {
  height: 180px;
}

@media (max-width: 768px) {
  .CardPokemonSelected {
    height: auto;
    width: 100%;
    margin: 0 auto 10px auto;
  }
  .CardPokemonSelected img {
    height: 100px;
  }
}

.type-badge {
  padding: 0.5em 1em;
  font-size: 0.9em;
  text-transform: capitalize;
}

.ability-badge {
  background-color: rgba(255, 255, 255, 0.2);
  padding: 0.35em 0.8em;
  font-size: 0.85em;
}

.stat-bar-container {
  max-width: 400px;
  margin: 0 auto;
}

.progress {
  background-color: rgba(0, 0, 0, 0.2);
}

.progress-bar {
  background-color: #fff;
}

/* Type colors - you can expand this with more types */
.type-normal {
  background-color: #a8a878;
}
.type-fire {
  background-color: #f08030;
}
.type-water {
  background-color: #6890f0;
}
.type-electric {
  background-color: #f8d030;
}
.type-grass {
  background-color: #78c850;
}
.type-ice {
  background-color: #98d8d8;
}
.type-fighting {
  background-color: #c03028;
}
.type-poison {
  background-color: #a040a0;
}
.type-ground {
  background-color: #e0c068;
}
.type-flying {
  background-color: #a890f0;
}
.type-psychic {
  background-color: #f85888;
}
.type-bug {
  background-color: #a8b820;
}
.type-rock {
  background-color: #b8a038;
}
.type-ghost {
  background-color: #705898;
}
.type-dragon {
  background-color: #7038f8;
}
.type-dark {
  background-color: #705848;
}
.type-steel {
  background-color: #b8b8d0;
}
.type-fairy {
  background-color: #ee99ac;
}

/* @media (max-width: 768px) {
    .CardPokemonSelected{
        height: 30vh;
        width: 40%;
        margin: 0 auto 10px auto;
    }
    .CardPokemonSelected img{
        height: 100px;
    }
} */
</style>
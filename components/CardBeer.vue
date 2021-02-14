<template>
  <div class="flex flex-wrap justify-items-center container m-auto">
    <div
      v-for="beer in beers"
      :key="beer.id"
      class="w-72 bg-white shadow-lg rounded-lg overflow-hidden my-20"
    >
      <nuxt-link :to="`/beers/${beer.route}`">go to</nuxt-link>
      <h3 class="text-gray-900 font-bold text-2xl uppercase">
        {{ beer.name }}
      </h3>
      <p class="text-gray-600 text-sm mt-1 capitalize">
        {{ beer.subtitle }}
      </p>
      <p class="text-gray-600 text-sm mt-1 capitalize">{{ beer.section }}</p>
      <p class="capitalize"><span>ABV:</span>{{ beer.abv }} <span>%</span></p>
      <div class="cover-container">
        <img
          class="h-full w-full object-cover mt-2"
          :src="beer.imgURL"
          :alt="beer.name"
        />
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: 'CardBeer',
  props: {
    beers: { type: Array, required: true },
  },
}
</script>

<style></style>

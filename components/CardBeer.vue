<template>
  <div class="">
    <div
      class="py-6 grid grid-cols-1 gap-4 md:grid-cols-2 lg:grid-cols-3 xl:grid-cols-4 m-10"
    >
      <div
        v-for="beer in beers"
        :key="beer.id"
        class="flex w-full bg-white shadow-lg rounded-lg overflow-hidden"
      >
        <div
          class="w-1/3 bg-cover"
          :style="`background-image: url('${beer.imgURL}')`"
        ></div>
        <div class="w-2/3 p-4">
          <h1 class="text-gray-900 font-bold text-2xl">{{ beer.name }}</h1>

          <p class="mt-2 text-gray-600 text-sm">
            {{ beer.subtitle }}
          </p>
          <p class="mt-2 text-gray-600 text-sm">
            {{ beer.abv }} <span>%</span>
          </p>

          <div class="flex item-center mt-2">
            <svg class="w-5 h-5 fill-current text-gray-700" viewBox="0 0 24 24">
              <path
                d="M12 17.27L18.18 21L16.54 13.97L22 9.24L14.81 8.63L12 2L9.19 8.63L2 9.24L7.46 13.97L5.82 21L12 17.27Z"
              />
            </svg>
            <svg class="w-5 h-5 fill-current text-gray-700" viewBox="0 0 24 24">
              <path
                d="M12 17.27L18.18 21L16.54 13.97L22 9.24L14.81 8.63L12 2L9.19 8.63L2 9.24L7.46 13.97L5.82 21L12 17.27Z"
              />
            </svg>
            <svg class="w-5 h-5 fill-current text-gray-700" viewBox="0 0 24 24">
              <path
                d="M12 17.27L18.18 21L16.54 13.97L22 9.24L14.81 8.63L12 2L9.19 8.63L2 9.24L7.46 13.97L5.82 21L12 17.27Z"
              />
            </svg>
            <svg class="w-5 h-5 fill-current text-gray-500" viewBox="0 0 24 24">
              <path
                d="M12 17.27L18.18 21L16.54 13.97L22 9.24L14.81 8.63L12 2L9.19 8.63L2 9.24L7.46 13.97L5.82 21L12 17.27Z"
              />
            </svg>
            <svg class="w-5 h-5 fill-current text-gray-500" viewBox="0 0 24 24">
              <path
                d="M12 17.27L18.18 21L16.54 13.97L22 9.24L14.81 8.63L12 2L9.19 8.63L2 9.24L7.46 13.97L5.82 21L12 17.27Z"
              />
            </svg>
          </div>
          <div class="flex item-center justify-between mt-3">
            <h1 class="text-gray-700 font-bold text-xl">{{ beer.section }}</h1>
            <nuxt-link
              class="px-3 py-2 bg-gray-800 text-white text-xs font-bold uppercase rounded"
              :to="`/beers/${beer.route}`"
              >Info</nuxt-link
            >
          </div>
        </div>
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

<template>
  <div>
    <div
      v-for="beer in data"
      :key="beer.id"
      class="min-w-screen min-h-screen bg-yellow-300 flex items-center p-5 lg:p-10 overflow-hidden relative"
    >
      <div
        class="w-full max-w-6xl rounded bg-white shadow-xl p-10 lg:p-20 mx-auto text-gray-800 relative md:text-left"
      >
        <div class="md:flex items-center -mx-10">
          <div class="w-full md:w-1/2 px-10 mb-10 md:mb-0">
            <div class="relative">
              <img
                :src="beer.imgURL"
                :alt="beer.name"
                class="w-full relative z-10 p-20"
              />
              <div
                class="border-4 border-yellow-200 absolute top-10 bottom-10 left-10 right-10 z-0"
              ></div>
            </div>
          </div>
          <div class="w-full md:w-1/2 px-10">
            <div class="mb-10">
              <h1 class="font-bold uppercase text-2xl mb-2">
                {{ beer.name }}
              </h1>
              <h2 class="font-semibold uppercase text-xl mb-5">
                {{ beer.subtitle }}
              </h2>
              <div class="flex">
                <h3 class="font-semibold uppercase text-lg mb-5 mr-4">
                  {{ beer.brewSheet.style }}
                </h3>
                <h3 class="font-semibold uppercase text-lg mb-5">
                  {{ beer.abv }} <span>%</span>
                </h3>
              </div>

              <p class="text-sm">
                {{ beer.description }}
              </p>
            </div>
            <div>
              <div class="inline-block align-bottom">
                <button
                  class="bg-yellow-300 opacity-75 hover:opacity-100 text-yellow-900 hover:text-gray-900 rounded-full px-10 py-2 font-semibold"
                >
                  <i class="mdi mdi-cart -ml-2 mr-2"></i> READ MORE!
                </button>
              </div>
            </div>
          </div>
        </div>
      </div>
    </div>
    <card-tasting-notes :notes="tastingNotes"></card-tasting-notes>
    <card-brew :sheets="brewSheet" :ingredients="ingredients"></card-brew>
  </div>
</template>

<script>
import CardBrew from '~/components/CardBrew.vue'
import CardTastingNotes from '~/components/CardTastingNotes.vue'
export default {
  components: { CardTastingNotes, CardBrew },
  async asyncData({ params, $http }) {
    const data = await $http.$get(
      `https://neopunkapi.herokuapp.com/api/beer/name/${params.name}`
    )
    data.forEach((beer) => {
      beer.name = beer.name.replace(/-/g, ' ')
      beer.subtitle = beer.subtitle.replace(/-/g, ' ').replace(/_/g, ' ')
      if (beer.brewSheet.hops !== null)
        beer.brewSheet.hops = beer.brewSheet.hops.map((hop) => {
          return hop.replace(/-/g, ' ')
        })
      if (beer.brewSheet.malts !== null)
        beer.brewSheet.malts = beer.brewSheet.malts.map((malt) => {
          return malt.replace(/-/g, ' ')
        })
      if (beer.brewSheet.style !== null)
        beer.brewSheet.style = beer.brewSheet.style.replace(/-/g, ' ')
      if (beer.ingredients !== null)
        beer.ingredients = beer.ingredients.map((ingredient) => {
          return ingredient.replace(/-/g, ' ')
        })
    })
    const tastingNotes = data.map((beer) => {
      return beer.tastingNotes
    })[0]
    const brewSheet = data.map((beer) => {
      return beer.brewSheet
    })[0]

    const ingredients = data.map((beer) => {
      return beer.ingredients
    })[0]

    return { data, tastingNotes, brewSheet, ingredients }
  },
}
</script>

<style></style>

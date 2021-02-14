<template>
  <!-- review item -->
  <div v-if="!checkSomeProps">
    <div class="mx-auto bg-white shadow-lg rounded-lg my-32 px-4 py-4 max-w-sm">
      <div class="mb-1 tracking-wide px-4 py-4">
        <h2 class="text-gray-800 font-semibold mt-1">{{ title }}</h2>
        <div class="-mx-8 px-8">
          <div v-if="colour" class="flex items-center mt-1">
            <div class="w-full">
              <div class="bg-gray-300 w-full rounded-lg h-2">
                <div
                  class="bg-indigo-600 rounded-lg h-2"
                  :class="widthColour"
                ></div>
              </div>
            </div>
          </div>
          <div v-if="hops" class="w-full flex capitalize mt-5">
            <div class="w-1/3 flex">
              <div>
                <p
                  class="py-1 px-2 rounded-full bg-indigo-600 text-sm text-gray-50"
                >
                  hops
                </p>
              </div>
            </div>
            <div class="w-2/3 flex flex-wrap">
              <div v-for="(hop, index) in hops" :key="index">
                <p class="m-1 py-1 px-2 rounded-full bg-indigo-200 text-sm">
                  {{ hop }}
                </p>
              </div>
            </div>
          </div>
          <div v-if="malts" class="w-full flex capitalize mt-5">
            <div class="w-1/3 flex">
              <div>
                <p
                  class="py-1 px-2 rounded-full bg-indigo-600 text-sm text-gray-50"
                >
                  malts
                </p>
              </div>
            </div>
            <div class="w-2/3 flex flex-wrap">
              <div v-for="(malt, index) in malts" :key="index">
                <p class="m-1 py-1 px-2 rounded-full bg-indigo-200 text-sm">
                  {{ malt }}
                </p>
              </div>
            </div>
          </div>
          <div v-if="ingredients" class="flex w-full capitalize">
            <div class="w-1/3 flex">
              <div>
                <p
                  class="py-1 px-2 rounded-full bg-indigo-600 text-sm text-gray-50"
                >
                  ingredients
                </p>
              </div>
            </div>
            <div class="w-2/3 flex flex-wrap">
              <div v-for="(ingredient, index) in ingredients" :key="index">
                <p class="m-1 py-1 px-2 rounded-full bg-indigo-200 text-sm">
                  {{ ingredient }}
                </p>
              </div>
            </div>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: 'CardBrew',
  props: {
    sheets: { type: Object, required: true },
    ingredients: {
      type: Array,
      default() {
        return ['-']
      },
    },
    title: { type: String, default: 'Brew Sheet' },
  },
  data() {
    return {
      checkSomeProps: !!(
        this.sheets.colour === null &&
        this.sheets.hops === null &&
        this.sheets.malts === null &&
        this.ingredients === null
      ),
      widthColour: `w-${Math.round(this.sheets.colour * 12)}/12`,
      colour: this.sheets.colour,
      hops: this.sheets.hops,
      malts: this.sheets.malts,
      style: this.sheets.style,
      ingredientsSheet: this.ingredients,
    }
  },
}
</script>

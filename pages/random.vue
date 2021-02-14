<template>
  <div
    class="min-w-screen min-h-screen bg-yellow-300 flex items-center p-5 lg:p-10 overflow-hidden relative"
  >
    <div
      class="w-full max-w-6xl rounded bg-white shadow-xl p-10 lg:p-20 mx-auto text-gray-800 relative md:text-left"
    >
      <div class="md:flex items-center -mx-10">
        <div class="w-full md:w-1/2 px-10 mb-10 md:mb-0">
          <div class="relative">
            <img
              src="beer.imgURL"
              alt="beer.name"
              class="w-full relative z-10 p-20"
            />
            <div
              class="border-4 border-yellow-200 absolute top-10 bottom-10 left-10 right-10 z-0"
            ></div>
          </div>
        </div>
        <div class="w-full md:w-1/2 px-10">
          <div class="mb-10">
            <h1 class="font-bold uppercase text-2xl mb-2">sfdhsfah</h1>
            <h2 class="font-semibold uppercase text-xl mb-5">afdhsdfh</h2>
            <div class="flex">
              <h3 class="font-semibold uppercase text-lg mb-5 mr-4">dfhdsfh</h3>
              <h3 class="font-semibold uppercase text-lg mb-5">
                zdhg <span>%</span>
              </h3>
            </div>

            <p class="text-sm">dsfhsdfh</p>
          </div>
          <div>
            <div class="inline-block align-bottom">
              <button
                class="bg-yellow-300 opacity-75 hover:opacity-100 text-yellow-900 hover:text-gray-900 rounded-full px-10 py-2 font-semibold"
                @click="random"
              >
                <i class="mdi mdi-cart -ml-2 mr-2"></i> GET DRUNK!
              </button>
            </div>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  methods: {
    async random({ $http }) {
      return await $http.$get(
        `https://neopunkapi.herokuapp.com/api/beer/random`
      )
    },
  },
}
</script>

<style></style>

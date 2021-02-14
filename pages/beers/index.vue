<template>
  <div>
    <card-beer :beers="beers"></card-beer>
  </div>
</template>

<script>
import CardBeer from '~/components/CardBeer'

export default {
  components: { CardBeer },
  async asyncData({ $http }) {
    const beers = await $http.$get('https://neopunkapi.herokuapp.com/api/beers')
    beers.forEach((beer) => {
      beer.route = beer.name
      beer.name = beer.name.replace(/-/g, ' ')
      beer.subtitle = beer.subtitle.replace(/-/g, ' ')
    })
    return { beers }
  },
}
</script>

<style></style>

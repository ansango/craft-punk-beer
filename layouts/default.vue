<template>
  <div>
    <navbar></navbar>
    <Nuxt />
  </div>
</template>
<script>
import Navbar from '~/components/Navbar'
export default {
  components: { Navbar },
  computed: {
    isHome() {
      return this.$route.name === '/'
    },
  },
}
</script>

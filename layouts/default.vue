<template>
  <div>
    <navbar></navbar>
    <Nuxt keep-alive />
  </div>
</template>
<script>
import Navbar from '~/components/Navbar'
export default {
  components: { Navbar },
}
</script>

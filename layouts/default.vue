<template>
  <div class="grid grid-cols-1">
    <Header />
    <nuxt />
    <!-- <Footer /> -->
  </div>
</template>
<script>
import Header from '~/components/Header'
// import Footer from '~/components/Footer'
export default {
  components: {
    Header
    // Footer
  }
}
</script>

<style></style>

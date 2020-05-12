<template>
  <div class="flex justify-between px-4 min-h-screen">
    <main class="flex-1 pt-20 pb-12">
      <div class="max-w-screen-xl mx-auto pr-4">
        <AddShout />
        <ContentWrapper />
      </div>
    </main>
    <Sidebar />
  </div>
</template>

<script>
import Sidebar from '~/components/Sidebar.vue'
import AddShout from '~/components/AddShout.vue'
import ContentWrapper from '~/components/ContentWrapper.vue'
export default {
  components: {
    Sidebar,
    AddShout,
    ContentWrapper
  }
}
</script>

<style>
/* Sample `apply` at-rules with Tailwind CSS
.container {
  @apply min-h-screen flex justify-center items-center text-center mx-auto;
}
*/
</style>

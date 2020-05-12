<template>
  <div>
    <CommentList />
    <CommentFrom />
  </div>
</template>
<script>
import CommentList from '~/components/comment/Comments-list.vue'
import CommentFrom from '~/components/comment/Comment-form.vue'
export default {
  components: {
    CommentList,
    CommentFrom
  }
}
</script>
<style scoped></style>

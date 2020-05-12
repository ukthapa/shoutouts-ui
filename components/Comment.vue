<template>
  <div>
    <CommentList v-if="haveComments" />
    <CommentFrom :section-info="sectionInfo" />
  </div>
</template>
<script>
import CommentList from '~/components/comment/Comments-list.vue'
import CommentFrom from '~/components/comment/Comment-form.vue'
export default {
  name: 'Comment',
  components: {
    CommentList,
    CommentFrom
  },
  props: {
    sectionInfo: {
      type: Array,
      default: () => []
    }
  },
  data() {
    return {
      haveComments: false
    }
  }
}
</script>
<style scoped></style>

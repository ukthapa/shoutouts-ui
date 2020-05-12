<template>
  <div
    class="border border-transparent  rounded opacity-25 hover:opacity-100 hover:border-gray-400 overflow-hidden transition duration-200 ease-in-out"
    :class="
      isCommentBoxActive
        ? 'border border-gray-400 divide-y divide-gray-400 opacity-100'
        : ''
    "
  >
    <ul v-if="commentsData.length > 0" class="commets-block p-3 overflow-auto">
      <li v-for="(comment, i) in commentsData" :key="i">
        <CommentList
          :id="sectionInfo[0]"
          :comments-data="JSON.parse(comment)"
        />
      </li>
    </ul>
    <CommentFrom v-if="isCommentBoxActive" :section-info="sectionInfo" />
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
    },
    isCommentBoxActive: {
      type: Boolean,
      default: () => false
    }
  },
  data() {
    return {
      commentsData: [],
      newList: null
    }
  },
  watch: {
    newList() {
      this.addComment()
    }
  },
  created() {
    this.$nuxt.$on('addComment', (newComment) => {
      this.newList = JSON.stringify(newComment)
    })
  },
  mounted() {
    if (localStorage.getItem('commentsData')) {
      try {
        this.commentsData = JSON.parse(localStorage.getItem('commentsData'))
      } catch (e) {
        localStorage.removeItem('commentsData')
      }
    }
  },
  methods: {
    addComment() {
      if (!this.newList) {
        return
      }
      this.commentsData.push(this.newList)
      this.newList = ''
      this.saveList()
    },
    saveList() {
      const parsed = JSON.stringify(this.commentsData)
      localStorage.setItem('commentsData', parsed)
    }
  }
}
</script>
<style scoped>
.commets-block {
  max-height: 230px;
}
</style>

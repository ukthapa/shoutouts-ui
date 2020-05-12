<template>
  <div
    ref="commentForm"
    class="comment-form-wrapper flex items-start border border-gray-400 rounded bg-gray-100 p-4"
  >
    <div class="profile-img-holder mr-2">
      <img
        src="../../assets/images/profiles/profile1.png"
        width="35"
        height="35"
        alt="Profile 1"
        class="rounded-full transition-shadow duration-200 ease-in-out hover:shadow"
      />
    </div>
    <div class="form-block">
      <div class="relative flex items-start">
        <textarea
          ref="input"
          name="text"
          class="w-full h-10 bg-gray-100 py-1 outline-none"
          placeholder="Leave a comment"
          @keyup="checkInput"
        />
        <button
          v-if="showCan"
          class="absolute mt-2 right-0 outline-none"
          @click="hideCommentBox"
        >
          <img
            src="../../assets/images/can-icon.svg"
            width="13"
            height="13"
            alt=""
          />
        </button>
      </div>
      <div class="form-footer" :class="isFormFooterVisible ? 'show' : 'hide'">
        <div class="flex items-center">
          <img
            src="../../assets/images/coin-icon.svg"
            width="22"
            height="22"
            alt=""
          />
          <input
            type="number"
            class="w-full bg-gray-100 p-2 outline-none"
            placeholder="Add Gold"
          />
        </div>
        <div class="flex flex-wrap items-center justify-between mt-4">
          <button class="outline-none">
            <img
              src="../../assets/images/smilly-icon.svg"
              width="22"
              height="22"
              alt=""
            />
          </button>
          <button class="outline-none">
            <img
              src="../../assets/images/image-icon.svg"
              width="22"
              height="22"
              alt=""
            />
          </button>
          <button class="outline-none">
            <img
              src="../../assets/images/gif-icon.svg"
              width="22"
              height="22"
              alt=""
            />
          </button>
          <button class="outline-none" @click="hideCommentBox">
            <img
              src="../../assets/images/can-icon.svg"
              width="13"
              height="13"
              alt=""
            />
          </button>
          <button
            class="bg-teal-500 hover:bg-teal-400 transition duration-500 ease-in-out  text-white uppercase shadow rounded focus:outline-none px-3 py-1"
          >
            Post
          </button>
        </div>
      </div>
    </div>
  </div>
</template>
<script>
export default {
  props: {
    sectionInfo: {
      type: Array,
      default: () => []
    }
  },
  data() {
    return {
      showCan: true,
      isFormFooterVisible: false
    }
  },
  mounted() {
    this.onFocus()
  },
  methods: {
    onFocus() {
      this.$nextTick(() => this.$refs.input.focus())
    },
    checkInput(event) {
      if (event.target.value !== '') {
        this.showCan = false
        this.isFormFooterVisible = true
      } else {
        this.showCan = true
        this.isFormFooterVisible = false
      }
    },
    hideCommentBox() {
      this.$nuxt.$emit('delectActiveBlockClass', this.sectionInfo)
      this.$nuxt.$emit('removeCommentBlock', false)
    }
  }
}
</script>
<style scoped>
.hide {
  height: 0;
  transition: all 0.5s ease-in-out;
  overflow: hidden;
}
.show {
  height: 100px;
  transition: all 0.5s ease-in-out;
  overflow: hidden;
}
</style>

<template>
  <div
    ref="commentForm"
    class="comment-form-wrapper flex items-start bg-gray-100 p-4"
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
          ref="commentNew"
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
            ref="addGold"
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
            @click="addComment"
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
      isFormFooterVisible: false,
      personList: [
        {
          fname: 'Jonathan Fields',
          profileImg: 'profile1.png',
          day: 1
        },
        {
          fname: 'Vijay Kaumar',
          profileImg: 'profile2.png',
          day: 2
        }
      ]
    }
  },
  mounted() {
    this.onFocus()
  },
  methods: {
    onFocus() {
      this.$nextTick(() => this.$refs.commentNew.focus())
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
    },
    addComment() {
      const num = Math.ceil(Math.random() * 2)
      const commentNew = {
        fname: this.personList[num - 1].fname,
        img: this.personList[num - 1].profileImg,
        id: this.sectionInfo[0],
        comment: this.$refs.commentNew.value,
        gold: this.$refs.addGold.value,
        day: Math.ceil(Math.random() * 10),
        hifi: Math.ceil(Math.random() * 4)
      }
      this.$nuxt.$emit('addComment', commentNew)
      this.hideCommentBox()
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

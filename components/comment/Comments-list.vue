<template>
  <div v-if="commentsData.id == id" class="comments-list">
    <div class="flex items-start v-line relative">
      <img
        :src="require(`@/assets/images/profiles/${commentsData.img}`)"
        width="45"
        height="45"
        :alt="commentsData.name"
        class="rounded-full border-2 border-white mr-2"
      />
      <div class="pb-3">
        <div ref="nameBlock" class="">
          <h1 class="text-sm font-medium">{{ commentsData.fname }}</h1>
          <div
            class="flex items-center text-gray-500 font-hairline text-xs mb-2"
          >
            <span class="mr-1 "
              >{{ commentsData.day }}
              {{ commentsData.day >= 1 ? 'day' : 'days ' }} ago</span
            >
            <span class="dot mr-1"></span>
            <span>Added {{ commentsData.gold || 0 }} Gold</span>
          </div>
          <div class="font-thin">{{ commentsData.comment }}</div>
          <div class="my-2 flex items-center justify-between">
            <div class="flex items-center justify-start">
              <div
                v-if="commentsData.hifi >= 0"
                class="flex items-center font-normal text-sm text-gray-600 hover:text-gray-700 border border-gray-200 hover:border-teal-400 bg-gray-200  hover:bg-teal-100 rounded-full px-2 py-0 mr-2 cursor-pointer"
              >
                <img
                  src="../../assets/images/hifi-icon.svg"
                  width="16"
                  height="16"
                  alt=""
                  class="mr-1"
                />
                <div>{{ commentsData.hifi }}</div>
              </div>
              <div
                class="flex items-center font-normal text-sm text-gray-600 hover:text-gray-700 border border-gray-200 hover:border-teal-400 bg-gray-200  hover:bg-teal-100 rounded-full px-2 py-0 mr-2 cursor-pointer"
              >
                <img
                  src="../../assets/images/face-icon.svg"
                  width="22"
                  height="22"
                  alt=""
                  class="mr-1"
                />
              </div>
            </div>
            <button class="flex items-center justify-end">
              <svg
                width="24"
                height="24"
                viewBox="0 0 24 24"
                fill="none"
                xmlns="http://www.w3.org/2000/svg"
                class="more-icon mx-auto"
              >
                <path
                  d="M12 8C13.1 8 14 7.1 14 6C14 4.9 13.1 4 12 4C10.9 4 10 4.9 10 6C10 7.1 10.9 8 12 8ZM12 10C10.9 10 10 10.9 10 12C10 13.1 10.9 14 12 14C13.1 14 14 13.1 14 12C14 10.9 13.1 10 12 10ZM12 16C10.9 16 10 16.9 10 18C10 19.1 10.9 20 12 20C13.1 20 14 19.1 14 18C14 16.9 13.1 16 12 16Z"
                  fill="#9D9D9D"
                />
              </svg>
            </button>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>
<script>
export default {
  props: {
    commentsData: {
      type: Object,
      default: () => []
    },
    id: {
      type: String,
      default: ''
    }
  }
}
</script>
<style>
.commets-block li .v-line::after {
  content: '';
  width: 2px;
  height: 100%;
  display: block;
  position: absolute;
  background: #ededed;
  left: 23px;
  z-index: -1;
}

.commets-block li:last-child .v-line::after {
  display: none;
}
</style>

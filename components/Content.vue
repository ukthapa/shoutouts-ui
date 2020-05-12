<template>
  <div>
    <div
      v-for="(shout, i) in shoutoutList"
      :id="shout.id"
      :key="i"
      class="grid grid-cols-6  lg:grid-cols-9 gap-4 py-6"
    >
      <div class="col-start-1 col-span-4 lg:col-start-3 lg:col-span-5 relative">
        <div
          class="card-wrapper"
          :class="{ active: i === activeItem }"
          @mouseenter="selectItem(i, shout.id)"
          @mouseleave="deselectItem(i, shout.id)"
        >
          <div
            id="toolbox"
            class="flex justify-content items-center absolute w-48 hidden divide-x divide-gray-300 hover:divide-gray-600 border border-gray-300 hover:border-gray-500 rounded-lg bg-white"
          >
            <button class="flex-grow">
              <svg
                width="24"
                height="24"
                viewBox="0 0 24 24"
                fill="none"
                xmlns="http://www.w3.org/2000/svg"
                class="face-tag-icon mx-auto"
              >
                <path
                  fill-rule="evenodd"
                  clip-rule="evenodd"
                  d="M11.992 4C7.576 4 4 7.584 4 12C4 16.416 7.576 20 11.992 20C16.416 20 20 16.416 20 12H18.4C18.4 15.536 15.536 18.4 12 18.4C8.464 18.4 5.6 15.536 5.6 12C5.6 8.464 8.464 5.6 12 5.6C12.3402 5.6 12.6742 5.62651 13 5.67758V4.06277C12.6698 4.02135 12.3334 4 11.992 4ZM17 8.0035V8H16.9972C16.9981 8.00117 16.9991 8.00234 17 8.0035ZM16 10C16 10.664 15.464 11.2 14.8 11.2C14.136 11.2 13.6 10.664 13.6 10C13.6 9.336 14.136 8.8 14.8 8.8C15.464 8.8 16 9.336 16 10ZM9.2 11.2C9.864 11.2 10.4 10.664 10.4 10C10.4 9.336 9.864 8.8 9.2 8.8C8.536 8.8 8 9.336 8 10C8 10.664 8.536 11.2 9.2 11.2ZM15.7997 14.2C15.0397 15.512 13.6237 16.4 11.9997 16.4C10.3757 16.4 8.95972 15.512 8.19972 14.2C8.04772 13.936 8.24772 13.6 8.55172 13.6H15.4477C15.7597 13.6 15.9517 13.936 15.7997 14.2Z"
                  fill="#CACACA"
                />
                <path
                  fill-rule="evenodd"
                  clip-rule="evenodd"
                  d="M19.0002 2C18.5584 2 18.2002 2.35817 18.2002 2.8V5.19995H15.8C15.3582 5.19995 15 5.55812 15 5.99995C15 6.44178 15.3582 6.79995 15.8 6.79995H18.2002V9.2C18.2002 9.64183 18.5584 10 19.0002 10C19.442 10 19.8002 9.64183 19.8002 9.2V6.79995H22.2C22.6418 6.79995 23 6.44178 23 5.99995C23 5.55812 22.6418 5.19995 22.2 5.19995H19.8002V2.8C19.8002 2.35817 19.442 2 19.0002 2Z"
                  fill="#CACACA"
                />
              </svg>
            </button>
            <button class="flex-grow" @click="openCommentBox(shout.id, i)">
              <svg
                width="20"
                height="20"
                viewBox="0 0 20 20"
                fill="none"
                xmlns="http://www.w3.org/2000/svg"
                class="comment-icon mx-auto"
              >
                <path
                  d="M20 2C20 0.9 19.1 0 18 0H2C0.9 0 0 0.9 0 2V14C0 15.1 0.9 16 2 16H16L20 20V2ZM14 9H11V12C11 12.55 10.55 13 10 13C9.45 13 9 12.55 9 12V9H6C5.45 9 5 8.55 5 8C5 7.45 5.45 7 6 7H9V4C9 3.45 9.45 3 10 3C10.55 3 11 3.45 11 4V7H14C14.55 7 15 7.45 15 8C15 8.55 14.55 9 14 9Z"
                  fill="#CACACA"
                />
              </svg>
            </button>
            <button class="flex-grow">
              <svg
                width="24"
                height="24"
                viewBox="0 0 24 24"
                fill="none"
                xmlns="http://www.w3.org/2000/svg"
                class="bookmark-icon mx-auto"
              >
                <path
                  d="M17 3H7C5.9 3 5 3.9 5 5V21L12 18L19 21V5C19 3.9 18.1 3 17 3Z"
                  fill="#CACACA"
                />
              </svg>
            </button>
            <button class="flex-grow">
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
          <div class="toolbox-shadow shodow-lg hidden absolute w-48"></div>
          <div class="card bg-white rounded-lg p-4 ml-16 cursor-pointer">
            <div class="card-header clearfix">
              <div class="shoutby">
                <img
                  :src="require(`@/assets/images/profiles/${shout.shoutByImg}`)"
                  width="45"
                  height="45"
                  :alt="shout.shoutBy"
                  class="h-12 w-12 rounded-full border-2 border-white "
                />
              </div>
              <div class="flex items-center">
                <div class="shoutto flex flex-row items-center">
                  <img
                    :src="
                      require(`@/assets/images/profiles/${shout.shoutToImg}`)
                    "
                    width="45"
                    height="45"
                    :alt="shout.shoutTo"
                    class="h-12 w-12 rounded-full border-2 border-white "
                  />
                  <div
                    v-if="shout.moreShouter > 1"
                    class="more-shouters h-12 w-12 rounded-full mx-auto flex items-center justify-center bg-gray-100 border-2 border-white text-gray-400 text-sm -ml-5"
                  >
                    +{{ shout.moreShouter }}
                  </div>
                </div>
                <div class="flex flex-col mx-2">
                  <div class="flex items-center divide-x divide-gray-200 ">
                    <div class="font-medium text-lg leading-none pr-2">
                      {{ shout.shoutBy }}
                      <span v-if="shout.moreShouter > 1"
                        >and {{ shout.moreShouter }} others</span
                      >
                    </div>
                    <div
                      class="flex items-center font-medium text-lg leading-none pl-2"
                    >
                      <img
                        src="../assets/images/coin-icon.svg"
                        width="16"
                        height="16"
                        alt=""
                        class="mr-1"
                      />
                      {{ shout.noOfGold }}
                    </div>
                  </div>
                  <div
                    class="flex items-center font-normal text-xs text-gray-500 mt-1"
                  >
                    <img
                      src="../assets/images/globe-icon.svg"
                      width="15"
                      height="15"
                      alt=""
                      class="mr-1 "
                    />
                    <div class="mr-1">{{ shout.shoutDay }},</div>
                    <div class="mr-1">
                      {{ shout.shoutMonth }} {{ shout.shoutDate }}
                    </div>
                    <div class="dot"></div>
                    <div class="ml-1">{{ shout.shoutTime }}</div>
                  </div>
                </div>
              </div>
            </div>
            <div
              class="card-body font-thin tracking-wide mt-4 mb-6 leading-relaxed"
              v-html="shout.shoutInfo"
            />
            <div class="card-footer">
              <div class="tags-wrapper flex items-center mb-6">
                <img
                  src="../assets/images/tag-icon.svg"
                  width="22"
                  height="22"
                  alt=""
                  class="mr-1 "
                />
                <div v-for="(tag, index) in shout.tags" :key="index">
                  <nuxt-link
                    :to="tag.url"
                    class="font-normal text-sm text-gray-600 hover:text-gray-700 bg-gray-200 rounded-full px-4 py-2 "
                  >
                    {{ tag.tag }}
                  </nuxt-link>
                </div>
              </div>
              <div class="reaction-wrapper flex items-center">
                <div
                  class="flex items-center font-normal text-sm text-gray-600 hover:text-gray-700 border border-gray-200 hover:border-teal-400 bg-gray-200  hover:bg-teal-100 rounded-full px-3 py-1 mr-2"
                >
                  <img
                    src="../assets/images/hifi-icon.svg"
                    width="16"
                    height="16"
                    alt=""
                    class="mr-1"
                  />
                  <div>{{ shout.hiFi }}</div>
                </div>
                <div
                  class="flex items-center font-normal text-sm text-gray-600 hover:text-gray-700 border border-gray-200 hover:border-teal-400 bg-gray-200  hover:bg-teal-100 rounded-full px-3 py-1 mr-2"
                >
                  <img
                    src="../assets/images/chart-icon.svg"
                    width="16"
                    height="16"
                    alt=""
                    class="mr-1"
                  />
                  <div>{{ shout.feed }}</div>
                </div>
                <div
                  class="flex items-center font-normal text-sm text-gray-600 hover:text-gray-700 border border-gray-200 hover:border-teal-400 bg-gray-200  hover:bg-teal-100 rounded-full px-3 py-1 mr-2"
                >
                  <img
                    src="../assets/images/face-icon.svg"
                    width="22"
                    height="22"
                    alt=""
                    class="mr-1"
                  />
                </div>
              </div>
            </div>
          </div>
        </div>
      </div>
      <div class="col-start-5 col-span-2 lg:col-start-8 lg:col-span-2">
        <Comment :class="isCommentActive ? 'active' : ''" />
      </div>
    </div>
  </div>
</template>
<script>
import Comment from '~/components/Comment.vue'
export default {
  components: {
    Comment
  },
  data() {
    return {
      activeItem: null,
      isCommentActive: false,
      shoutoutList: [
        {
          id: 'shout-1',
          shoutBy: 'Jonathan',
          shoutByImg: 'profile1.png',
          shoutTo: 'Vijay Kumar',
          shoutToImg: 'profile2.png',
          moreShouter: 0,
          noOfGold: '20',
          shoutDay: 'Monday',
          shoutMonth: 'August',
          shoutDate: 17,
          shoutTime: '4:34 PM',
          shoutInfo:
            'Thank you for going above and beyond on all the goals and KPIs this week! In case anyone else was curious, check out this dash here: <a href="https://app.periscopedata.com/app/joinassembly/389362">https://app.periscopedata.com/app/joinassembly/389362</a>',
          tags: [
            {
              tag: 'KPIs',
              url: '/'
            }
          ],
          hiFi: 1,
          feed: 15
        },
        {
          id: 'shout-2',
          shoutBy: 'Jonathan',
          shoutByImg: 'profile2.png',
          shoutTo: 'Jonathan Fields',
          shoutToImg: 'profile1.png',
          moreShouter: 2,
          noOfGold: '5 each',
          shoutDay: 'TuesDay',
          shoutMonth: 'August',
          shoutDate: 4,
          shoutTime: '10:34 AM',
          shoutInfo:
            '222Thank you for going above and beyond on all the goals and KPIs this week! In case anyone else was curious, check out this dash here: <a href="https://app.periscopedata.com/app/joinassembly/389362">https://app.periscopedata.com/app/joinassembly/389362</a>',
          tags: [
            {
              tag: 'KPIs',
              url: '/'
            }
          ],
          hiFi: 1,
          feed: 15
        }
      ]
    }
  },
  methods: {
    selectItem(i, id) {
      const elem = document
        .getElementById(id)
        .getElementsByClassName('card-wrapper')[0]
        .className.split(' ')
      if (!elem.includes('active-block')) {
        this.activeItem = i
      }
    },
    deselectItem(i, id) {
      const elem = document
        .getElementById(id)
        .getElementsByClassName('card-wrapper')[0]
        .className.split(' ')
      if (!elem.includes('active-block')) {
        this.activeItem = null
      }
    },
    openCommentBox(id) {
      document
        .getElementById(id)
        .getElementsByClassName('card-wrapper')[0]
        .classList.add('active-block')
      this.isCommentActive = true
    }
  }
}
</script>
<style>
.card .card-body a {
  @apply text-teal-400;
  word-break: break-all;
}
.card .card-body a:hover {
  @apply underline;
}

#toolbox,
.toolbox-shadow {
  right: 10px;
}

.toolbox-shadow {
  z-index: -1;
  height: 42px;
  border-radius: 0.5rem;
}

.card-wrapper .card {
  transition: all 0.2s ease-in-out;
}

.card-wrapper.active .card {
  box-shadow: 0px 10px 25px rgba(202, 202, 202, 0.5);
  transform: translateY(-2px);
}

.card-wrapper.active #toolbox {
  display: flex;
  top: -1.8rem;
  animation-name: showuptoolbox;
  animation-duration: 1.5s;
  z-index: 10;
}

.card-wrapper.active .toolbox-shadow {
  display: block;
  box-shadow: -1px 9px 13px #e4dddd;
}

@keyframes showuptoolbox {
  0% {
    opacity: 0;
    top: 0;
    z-index: -1;
  }
  25% {
    opacity: 0.75;
    top: -3rem;
    z-index: -1;
  }
  50% {
    opacity: 1;
    top: -1.8rem;
    z-index: 10;
  }
  100% {
    opacity: 1;
    top: -1.8rem;
    z-index: 10;
  }
}

#toolbox:hover {
  box-shadow: 0px 2px 0px #9d9d9d;
}

#toolbox button svg path {
  transition: all 0.2s ease-in-out;
}

#toolbox:hover button svg path {
  fill: #9d9d9d;
}

#toolbox:hover button:hover .face-tag-icon path {
  fill: #f6ad55;
}

#toolbox:hover button:hover .comment-icon path {
  fill: #00bbd1;
}

#toolbox:hover button:hover .bookmark-icon path {
  fill: #38a169;
}

#toolbox:hover button:hover .more-icon path {
  fill: #3182ce;
}

#toolbox button {
  padding: 5px;
  height: 40px;
}

.shoutby {
  float: left;
  margin-left: -74px;
  position: relative;
  transition: all 0.2s ease-in-out;
}
.shoutby:after {
  content: '';
  width: 0;
  height: 0;
  border-top: 7px solid transparent;
  border-bottom: 7px solid transparent;
  border-left: 10px solid #ccc;
  position: absolute;
  right: -19px;
  top: 50%;
  transform: translateY(-50%);
}

.card-wrapper.active .shoutby {
  margin-left: -90px;
}
.card-wrapper.active .shoutby:after {
  border-left: 10px solid #9e9d9d;
}

.dot {
  height: 3px;
  width: 3px;
  background-color: #bbb;
  border-radius: 50%;
  display: inline-block;
}
</style>

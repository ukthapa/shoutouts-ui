<template>
  <div>
    <div
      v-for="shout in shoutoutList"
      :key="shout.id"
      class="grid grid-cols-6  lg:grid-cols-9 gap-4 py-4"
    >
      <div
        :id="shout.id"
        class="col-start-1 col-span-4 lg:col-start-3 lg:col-span-5"
      >
        <div
          class="card bg-white rounded-lg p-4 ml-16  border border-transparent transition duration-500 ease-in-out cursor-pointer"
          :class="
            isActive
              ? 'hover:shadow-xl hover:border-gray-200 hover:border-opacity-75 transform hover:-translate-y-1'
              : ''
          "
          @mouseover="addHoverClass"
        >
          <div>Testing</div>
          <div class="card-header flex transform -translate-x-16">
            <div>Testing</div>
            <div>Testing</div>
            <div>Test</div>
          </div>
          <div
            class="card-body font-thin tracking-wide"
            v-html="shout.shoutInfo"
          />
          <div class="card-footer"></div>
        </div>
      </div>
      <div class="col-start-5 col-span-2 lg:col-start-8 lg:col-span-2">
        Test
      </div>
    </div>
  </div>
</template>
<script>
export default {
  data() {
    return {
      isActive: false,
      shoutoutList: [
        {
          id: 'shout-1',
          shoutBy: 'Jonathan',
          shoutByImg: '../assets/images/profiles/profile2.png',
          shoutTo: 'Vijay Kumar',
          shoutToImg: '../assets/images/profiles/profile.png',
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
          shoutTo: 'Jonathan Fields and 2 others',
          noOfGold: '5 each',
          shoutDay: 'TuesDay',
          shoutMonth: 'August',
          shoutDate: 4,
          shoutTime: '10:34 AM',
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
        }
      ]
    }
  },
  methods: {
    addHoverClass() {
      this.isActive = true
    }
  }
}
</script>
<style>
.card a {
  @apply text-blue-400;
  word-break: break-all;
}
.card a:hover {
  @apply underline;
}
</style>

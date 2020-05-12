<template>
  <div>
    <div v-for="(shout, i) in shoutoutList" :id="shout.id" :key="i">
      <Content :shout="[shout, i]" />
    </div>
  </div>
</template>
<script>
import Content from '~/components/Content.vue'
export default {
  components: {
    Content
  },
  data() {
    return {
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
  }
}
</script>
<style></style>

<template>
  <div>
    <h1>Events</h1>
    <EventCard
      v-for="(event, index) in events"
      :key="index"
      :event="event"
      :data-index="index"
    />
  </div>
</template>
<script>
import EventCard from '@/components/EventCard.vue'
export default {
  components: {
    EventCard,
  },
  asyncData({ $axios, error }) {
    // console.log('/asyncData')
    return $axios
      .get('http://localhost:3000/events')
      .then((res) => ({
        events: res.data,
      }))
      .catch((e) => {
        error({
          statusCode: 503,
          message: 'Unable to fetch events at this time. Please try again.',
        })
      })
  },
  head() {
    return {
      title: 'Event Listing',
    }
  },
}
</script>

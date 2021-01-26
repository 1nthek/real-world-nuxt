<template>
  <div>
    <h1>Event #{{ id }}</h1>
  </div>
</template>

<script lang="ts">
import Vue from 'vue'

export default Vue.extend({
  head() {
    return {
      title: 'Event #' + this.$route.params.id,
      meta: [
        {
          hid: 'description',
          name: 'description',
          content:
            'What you need to know about event #' + this.$route.params.id,
        },
      ],
    }
  },
  computed: {
    id() {
      return this.$route.params.id
    },
  },
})
</script>

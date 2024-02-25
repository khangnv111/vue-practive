<template>
  <section>
    FILTER
  </section>
  <section>
    <base-card>
      <div class="controls">
        <base-button mode="outline">Refresh</base-button>
        <base-button link to="/register">Register as Coach</base-button>
      </div>
      <ul v-if="hasCoaches">
        <coach-item-vue v-for="item in filterCoaches" :key="item.id" :id="item.id" :firstName="item.firstName"
          :lastName="item.lastName" :rate="item.hourlyRate" :areas="item.areas"></coach-item-vue>
      </ul>
      <h1 v-else>No Coaches found.</h1>
    </base-card>

  </section>
</template>

<script>
import CoachItemVue from '@/components/coaches/CoachItem.vue'
import BaseCard from '@/components/ui/BaseCard.vue'
import BaseButton from '@/components/ui/BaseButton.vue'

export default {
  components: {
    CoachItemVue,
    BaseCard,
    BaseButton
  },
  computed: {
    filterCoaches() {
      return this.$store.getters['coaches/coaches']
      // return []
    },
    hasCoaches() {
      return this.$store.getters['coaches/hasCoaches']
    }
  }
}
</script>

<style scoped>
ul {
  list-style: none;
  margin: 0;
  padding: 0;
}

.controls {
  display: flex;
  justify-content: space-between;
}
</style>
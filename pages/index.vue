<template>
  <div class="container">
    <TheMenu :home-is-active="homeIsActive" @action="toggleDisplay" />
    <main>
      <TheHeading :elephant-is-visible="!homeIsActive" />
      <TheTable v-if="homeIsActive" @trumpet="updateDisplay" />
      <TheElephant v-else :elephant="elephant" />
    </main>
  </div>
</template>

<script>
export default {
  name: 'IndexPage',
  data() {
    return {
      homeIsActive: true,
      elephant: {}
    }
  },
  methods: {
    toggleDisplay(button) {
      button === 'home' ? this.homeIsActive = true : this.homeIsActive = false
    },
    updateDisplay(elephant) {
      this.elephant = elephant
      this.homeIsActive = false
    }
  }
}
</script>

<style scoped>
@media screen and (min-width: 1000px) {
  main {
    margin-left: 361px;
  }
}
</style>

<template>
  <div class="container">
    <TheMenu @action="toggleDisplay" />
    <main>
      <TheHeading :elephant-is-visible="!homeIsActive" />
    </main>
  </div>
</template>

<script>
export default {
  name: 'IndexPage',
  data() {
    return {
      homeIsActive: true
    }
  },
  methods: {
    toggleDisplay(button) {
      button === 'home' ? this.homeIsActive = true : this.homeIsActive = false
    }
  }
}
</script>

<style scoped>
@media screen and (max-width: 999px) {
  main {
    margin-top: calc(100px + 1vw);
  }
}
@media screen and (min-width: 1000px) {
  main {
    margin-left: 361px;
  }
}
</style>

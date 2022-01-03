<template>
  <nav>
    <div class="logo">
      <div class="img-container">
        <img src="~/assets/elephant.png" alt="elephant logo">
      </div>
    </div>
    <button :class="{ active: homeIsActive }" @click="toggleActive('home')">
      Home
    </button>
    <button :class="{ active: !homeIsActive }" @click="toggleActive('elephant')">
      Elephant
    </button>
  </nav>
</template>

<script>
export default {
  props: {
    homeIsActive: {
      type: Boolean,
      required: false,
      default: true
    }
  },
  methods: {
    toggleActive(button) {
      this.$emit('action', button)
    }
  }
}
</script>

<style scoped>
@media screen and (max-width: 999px) {
  nav {
    padding: 0 calc(20px + 1vw);
    grid-template-columns: repeat(3, max-content);
    column-gap: calc(10px + 1vw);
  }

  .logo {
    margin: 15px calc(5px + 1vw) 15px 0;
    width: calc(70px + 1vw);
    height: calc(70px + 1vw);
  }

  button {
    padding: 0 10px;
  }
}
@media screen and (min-width: 1000px) {
  nav {
    position: fixed;
    top: 0;
    left: 0;
    width: 361px;
    height: 100vh;
    grid-template-rows: repeat(3, max-content);
  }

  .logo {
    margin: 60px 85px;
    width: 191px;
    height: 191px;
  }

  button {
    width: 100%;
    padding: 17px 56px;
    text-align: left;
  }
}

nav {
  display: grid;
  background-color: #B9B9FF80;
  z-index: 2;
}

.logo {
  position: relative;
  border-radius: 50%;
  background-color: #FFF;
}

.logo .img-container {
  position: absolute;
  top: 19%;
  left: 17%;
  right: 17%;
}

.img-container img {
  width: 100%;
}

button {
  border: 0;
  background: transparent;
  font-size: 18px;
  line-height: 28px;
  cursor: pointer;
  color: #30425A;
  -webkit-tap-highlight-color: transparent;
}

.active {
  color: #FFF;
  background-color: #B9B9FF;
}
</style>
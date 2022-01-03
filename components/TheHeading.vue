<template>
  <h1>
    Acumen Digital Interview Task / Elephantom
    <span v-if="elephantIsVisible">
      <svg width="12" height="14" viewBox="0 0 12 14" fill="none" xmlns="http://www.w3.org/2000/svg">
        <path d="M1 1L10 6.56616L1 13" stroke="#919EAB" stroke-width="2"/>
      </svg>
      Elephant
    </span>
  </h1>
</template>

<script>
export default {
  props: {
    elephantIsVisible: {
      type: Boolean,
      required: false,
      default: false
    }
  }
}
</script>

<style scoped>
h1 {
  margin: 0;
  padding: 34px 35px 31px;
  font-size: 18px;
  font-weight: normal;
  line-height: 28px;
  color: #30425A;
  background-color: #FFF;
  box-shadow: 0 -7px 24px #00000040;
}

svg {
  margin: 0 14px;
}
</style>
<template>
  <div class="container">
    <div class="img-container">
      <img :src="elephant.image" :alt="`${elephant.sex} ${elephant.name}`">
    </div>
    <div class="texts">
      <h2>
        {{ elephant.name }}
      </h2>
      <p>
        {{ elephant.sex }}
      </p>
    </div>
    <p>
      {{ elephant.note }}
    </p>
  </div>  
</template>

<script>
export default {
  props: {
    elephant: {
      type: Object,
      required: false,
      default() {}
    }
  }
}
</script>

<style scoped>
.container {
  padding: 32px 55px;
}

.img-container {
  position: relative;
  width: 100%;
}

.img-container img {
  width: 100%;
}

.img-container::after {
  position: absolute;
  top: 0;
  left: 0;
  bottom: 6px;
  width: 100%;
  content: '';
  background: linear-gradient(180deg, #C4C4C400 -1.55%, #1D1DF25E 77.84%);
}

.texts {
  border-bottom: 1px solid #C4CDD59E;
  padding: 29px 0 17px;
  display: grid;
  grid-template-columns: repeat(2, max-content);
  align-items: baseline;
  column-gap: 16px;
}

h2 {
  margin: 0;
  font-size: 48px;
  font-weight: bold;
  line-height: 74px;
  color: #30425A;
}

p {
  margin: 0;
  font-size: 18px;
  font-weight: normal;
  line-height: 28px;
  color: #30425A;
}

.container > p {
  margin-top: 20px;
  font-size: 24px;
  line-height: 37px;
}
</style>
<template>
  <div class="container">
    <div class="img-container">
      <img src="~/assets/tuffi.png" alt="female tuffi">
    </div>
    <div class="texts">
      <h2>
        Tuffi
      </h2>
      <p>
        Female
      </p>
    </div>
    <p>
      A female circus elephant that became famous in Germany during 1950 when she accidentally fell into the River Wupper, and survived.
    </p>
  </div>  
</template>

<style scoped>
.container {
  padding: 32px 55px;
}

.img-container {
  position: relative;
  width: 100%;
  padding-top: 45.6%;
}

.img-container img {
  position: absolute;
  width: 100%;
  top: 0;
  left: 0;
}

.img-container::after {
  position: absolute;
  top: 0;
  left: 0;
  width: 100%;
  height: 100%;
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
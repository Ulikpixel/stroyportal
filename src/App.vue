<template>
  <router-view />
</template>

<style lang="scss">
@import "./assets/scss/index.scss";

* {
  box-sizing: border-box;
  margin: 0;
  padding: 0;
}

.container {
  max-width: 1142px;
  width: 100%;
  margin: 0 auto;
  padding: 0 15px !important;
}

ul {
  list-style-type: none;
}

button, input {
  outline: none;
}
</style>

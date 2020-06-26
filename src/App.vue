<template>
  <div id="app">
    <router-view />
  </div>
</template>

<style lang="scss">
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
}

@font-face {
  font-family: "RuneScape UF";
  src: url("/font/RuneScape-UF.woff2") format("woff2"),
    url("/font/RuneScape-UF.woff") format("woff"),
    url("/font/RuneScape-UF.ttf") format("truetype");
  font-weight: normal;
  font-style: normal;
  font-display: swap;
}
</style>

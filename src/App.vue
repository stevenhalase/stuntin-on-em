<template>
  <div id="app">
    <!-- <div id="nav">
      <router-link to="/styleguide">Styleguide</router-link>
    </div> -->
    <router-view/>
  </div>
</template>

<style lang="scss">
#app {
  width: 100vw;
  height: 100vh;
  background: #232526;
  background: -webkit-linear-gradient(to top, #414345, #232526);
  background: linear-gradient(to top, #414345, #232526);
}
</style>

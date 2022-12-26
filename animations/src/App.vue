<template>
  <div>
    <button @click="flag = !flag">Toggle</button>
    <transition name="fade" mode="out-in">
      <h2 v-if="flag" key="main">Brace for your death</h2>
      <h2 v-else key="secondary">Oh Wrong Universe</h2>
    </transition>
    <transition-group name="fade" mode="out-in">
      <ul v-for="item in Object.keys(items)" :key="item.key">
        <li >{{item}} ->  {{items[item]}}</li>
      </ul>    
    </transition-group>
  </div>
</template>

<script>
export default {
  name: "App",
  data() {
    return {
      flag: false,
      items: {
        a: 1,
        b: 2,
        c: 3,
      },
    };
  },
};
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}

.fade-enter-from {
  opacity: 0;
}

.fade-enter-active {
  transition: all 0.25s linear;
}

.fade-leave-from {
  opacity: 100%;
}

.fade-leave-to {
  transition: all 0.25s linear;
  opacity: 0;
}
</style>

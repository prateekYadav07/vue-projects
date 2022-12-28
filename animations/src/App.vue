<template>
  <div>
    <button @click="flag = !flag">Toggle</button>
    <!-- <transition name="fade" mode="out-in">
      <h2 v-if="flag" key="main">Brace for your death</h2>
      <h2 v-else key="secondary">Oh Wrong Universe</h2>
    </transition>
    <transition-group name="fade" mode="out-in">
      <ul v-for="item in Object.keys(items)" :key="item.key">
        <li >{{item}} ->  {{items[item]}}</li>
      </ul>    
    </transition-group> -->

    <transition name="zoom">
      <h2 v-if="flag">Hello</h2>
    </transition>
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

h2 {
  width: 400px;
  padding: 20px;
  margin: 20px;
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

.zoom-enter-active{
  animation: zoom-in 1s linear forwards;
  transition: all 1s linear;
}

.zoom-leave-active{
  animation: zoom-out 1s linear forwards;
}

@keyframes zoom-in {
  from {
    transform: scale(0, 0);
  }
  to {
    transform: scale(1, 1);
  }
}

@keyframes zoom-out {
  from {
    transform: scale(1, 1);
  }
  to {
    transform: scale(0, 0);
  }
}
</style>

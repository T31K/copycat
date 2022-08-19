<template>
  <div id="app">
    <div v-for="(item, key) in list" :key="key">
      {{ item }}
    </div>
  </div>
</template>

<script>
export default {
  name: "App",
  data() {
    return {
      list: [1, 2, 3],
    };
  },
  mounted() {
    this.receiveMessage();
  },
  methods: {
    receiveMessage() {
      window.ipcRenderer.receive("defaultChannel", (message) => {
        console.log(message); // Prints 'whoooooooh!'
      });
    },
  },
};
</script>

<style>
#app {
  height: 800px;
  width: 600px;
}
</style>

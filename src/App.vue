<template>
  <div id="app">
    <div id="hello-node">
        {{ message }}
    </div>
    <hr />
    <button @click="handleClick">Click</button>
  </div>
</template>

<script>
export default {
  name: "App",
  data: () => ({
    message: "Start!",
  }),
  computed: {
    helloNode() {
      return document.getElementById('hello-node');
    },
  },
  methods: {
    handleClick() {
      this.handleTimeout();
      this.handleNextTick();
    },
    handleTimeout() {
      this.message = "setTimeout 1!";
      console.log("handleTimeout:", this.helloNode.innerText);
      this.message = "setTimeout 2!";
      console.log("handleTimeout:", this.helloNode.innerText);

      setTimeout(() => {
        this.message = "setTimeout end!";
        console.log("handleTimeout:", this.helloNode.innerText);
      });
    },
    handleNextTick() {
      this.message = "nextTick 1!";
      console.log("handleNextTick:", this.helloNode.innerText);
      this.message = "nextTick 2!";
      console.log("handleNextTick:", this.helloNode.innerText);

      this.$nextTick(() => {
        this.message = "nextTick end!";
        console.log("handleNextTick:", this.helloNode.innerText);
      });
    },
  },
};
</script>

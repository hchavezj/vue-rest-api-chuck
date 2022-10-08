<template>
  <div class="home">
    <h1>👊 Chuck Norris Fact</h1>
    <div v-if="chuckFact" class="fact">
      <i>"{{ chuckFact }}"</i>
    </div>
    <button @click="showFact()">Get Fact</button>
  </div>
</template>

<script scope>
// @ is an alias to /src
// import HelloWorld from "@/components/HelloWorld.vue";

import axios from "axios";

export default {
  name: "HomeView",
  props: {
    msg: String,
  },
  data() {
    return {
      chuckFact: "",
    };
  },
  methods: {
    async showFact() {
      let config = {
        headers: {
          Accept: "application/json",
        },
      };
      const chuckFact = await axios.get(
        "https://api.chucknorris.io/jokes/random",
        config
      );
      this.chuckFact = chuckFact.data.value;
    },
  },
};
</script>

<style scope>
.fact {
  margin-top: 2rem;
  margin-bottom: 2rem;
  font-size: 1.5rem;
}
.home button {
  font-size: 1.2rem;
  background-color: #4293b9;
  border: 2px solid #4293b9;
  color: white;
  border-radius: 4px;
  transition-duration: 0.4s;
}
.home button:hover {
  background-color: white;
  color: #4293b9;
}
</style>

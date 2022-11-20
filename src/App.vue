<script lang="ts">
import { defineComponent } from "vue";
import axios from "axios";

const baseUrl = import.meta.env.VITE_APP_BASE_URL;

interface Props {
  name: string;
  values: string;
  isLoading: boolean;
}

export default defineComponent({
  data(): Props {
    return {
      name: "",
      values: "",
      isLoading: false,
    };
  },
  computed: {},
  methods: {
    async submitName(): Promise<void> {
      this.isLoading = true;
      const result = await axios(`${baseUrl}${this.name}`);
      const value = result.data;
      this.values = value?.value;
      this.isLoading = false;
    },
  },
});
</script>

<template>
  <div class="container">
    <div class="header">
      Get the random jokes, with your name in this shit site
    </div>
    <div class="card" ref="card">
      <div>Submit Your Name here</div>
      <div v-if="isLoading">Loading ....</div>
      <div class="result" v-else>{{ values }}</div>
      <div class="input-name">
        <input v-model="name" type="text" />
        <button class="button-add" @click="submitName">Submit</button>
      </div>
    </div>
  </div>
  <section>
    <span></span>
    <span></span>
    <span></span>
    <span></span>
    <span></span>
    <span></span>
    <span></span>
    <span></span>
    <span></span>
    <span></span>
  </section>
</template>

<style scoped>
.container {
  margin: 50px auto;
  z-index: 99;
  text-align: center;
  font-family: "Nunito", sans-serif;
  position: relative;
  overflow: hidden;
}

.header {
  font-weight: 700;
  font-size: 25px;
  margin: 20px 0px;
  color: rgb(210, 206, 206);
}

.card {
  padding: 30px;
  border: 1px solid #b2b2b2;
  border-radius: 10px;
  height: auto;
  width: 330px;
  margin: auto;
  background-color: #f9f9f9;
  box-shadow: 1px 1px 2px rgba(0, 0, 0, 0.5);
}

.button-add {
  color: white;
  background-color: #49beb7;
  border: none;
  padding: 1px 10px;
  border-radius: 3px;
  cursor: pointer;
}

.button-add:hover {
  background-color: #57b5af;
  color: rgb(209, 201, 201);
}

.button-add:focus {
  outline: nones;
}

input[type="text"] {
  padding: 5px;
  margin-right: 20px;
  border: 2px solid #c7f2a4;
  border-radius: 5px;
  font-family: "Nunito", sans-serif;
  box-shadow: 1px 1px 2px 1px rgba(0, 0, 0, 0.06);
}

input[type="text"]:focus {
  outline: none;
  border: 2px solid #a460ed;
}

.input-name {
  display: flex;
  justify-content: center;
  padding: 10px 0px;
}
.result {
  padding: 15px 0;
}
section {
  position: absolute;
  top: 0;
  left: 0;
  width: 100%;
  height: 100vh;
  background: url("./assets/img/space-nas.png");
  background-color: black;
  background-position-x: center;
  background-size: cover;
  animation: animateBg 50s linear infinite;
  overflow: hidden;
}
@keyframes animateBg {
  0%,
  100% {
    transform: scale(1);
  }
  50% {
    transform: scale(1.2);
  }
}
span {
  position: absolute;
  top: 50%;
  left: 50%;
  width: 4px;
  height: 4px;
  background: #fff;
  border-radius: 50%;
  box-shadow: 0 0 0 4px rgba(255, 255, 255, 0.1),
    0 0 0 8px rgba(255, 255, 255, 0.1), 0 0 20px rgba(255, 255, 255, 1);
  animation: animate 3s linear infinite;
}
span::before {
  content: "";
  position: absolute;
  top: 50%;
  transform: translateY(-50%);
  width: 300px;
  height: 1px;
  background: linear-gradient(90deg, #fff, transparent);
}
@keyframes animate {
  0% {
    transform: rotate(315deg) translateX(0);
    opacity: 1;
  }
  70% {
    opacity: 1;
  }
  100% {
    transform: rotate(315deg) translateX(-1500px);
    opacity: 0;
  }
}
span:nth-child(1) {
  top: 0;
  right: 0;
  left: initial;
  animation-delay: 0;
  animation-duration: 1s;
}

span:nth-child(2) {
  top: 0;
  right: 80px;
  left: initial;
  animation-delay: 0.2s;
  animation-duration: 3s;
}

span:nth-child(3) {
  top: 80px;
  right: 0px;
  left: initial;
  animation-delay: 0.4s;
  animation-duration: 2s;
}

span:nth-child(4) {
  top: 0;
  right: 180px;
  left: initial;
  animation-delay: 0.6s;
  animation-duration: 1.5s;
}

span:nth-child(5) {
  top: 0;
  right: 400px;
  left: initial;
  animation-delay: 0.8s;
  animation-duration: 2.5s;
}

span:nth-child(6) {
  top: 0;
  right: 600px;
  left: initial;
  animation-delay: 1s;
  animation-duration: 3s;
}
span:nth-child(7) {
  top: 300px;
  right: 0px;
  left: initial;
  animation-delay: 1s;
  animation-duration: 1.75s;
}

span:nth-child(8) {
  top: 0px;
  right: 700px;
  left: initial;
  animation-delay: 1.4s;
  animation-duration: 1.25s;
}

span:nth-child(9) {
  top: 0px;
  right: 1000px;
  left: initial;
  animation-delay: 0.75s;
  animation-duration: 2.25s;
}

span:nth-child(10) {
  top: 0px;
  right: 1000px;
  left: initial;
  animation-delay: 2.75s;
  animation-duration: 2.25s;
}
</style>

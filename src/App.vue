<template>
  <div class="modal-bg" v-if="modalOpen === true" @click="modalOpen = false">
    <div class="modal-content">
      <h4>상세페이지</h4>
      <p>상세페이지</p>
    </div>
  </div>

  <div class="tab">
    <a v-for="(el, i) in tabs" :key="i">{{ el }}</a>
  </div>

  <div v-for="(el, i) in roomData" :key="i" @click="modalOpen = true">
    <img :src="el.image" class="room-img" />
    <h4>{{ el.title }}</h4>
    <p>월 {{ el.price }}원</p>
    <button @click="report[i]++">허위매물신고</button>
    <span>신고수 : {{ report[i] }}</span>
  </div>
</template>

<script>
import roomData from "./assets/roomData";

export default {
  name: "App",
  data() {
    return {
      modalOpen: false,
      tabs: ["Home", "Shop", "About"],
      report: [0, 0, 0],
      roomData: roomData,
    };
  },
  components: {},
};
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
}

body {
  margin: 0;
}

div {
  box-sizing: border-box;
}

.tab {
  background-color: purple;
  padding: 10px;
  display: flex;
  align-items: center;
  justify-content: space-around;
}

.tab a {
  color: white;
}

.room-img {
  width: 70%;
  margin-top: 40px;
}

.modal-bg {
  position: fixed;
  width: 100%;
  height: 100%;
  background-color: rgba(0, 0, 0, 0.5);
  padding: 30px;
}

.modal-content {
  position: relative;
  top: 30%;
  width: 100%;
  border-radius: 20px;
  background-color: white;
  padding: 30px;
}
</style>

<template>
  <transition name="fade">
    <Modal
      @closeModal="모달창열렸니 = false"
      :원룸들="원룸들"
      :pushButton="pushButton"
      :모달창열렸니="모달창열렸니"
  /></transition>
  <div class="menu">
    <a v-for="작명 in 메뉴들" :key="작명">{{ 작명 }}</a>
  </div>

  <Discount :discountNumber="discountNumber" v-if="showDiscount == true" />

  <button @click="priceSort">가격순정렬</button>
  <button @click="sortBack">되돌리기</button>

  <Card
    @openModal="
      모달창열렸니 = true;
      pushButton = index;
    "
    :원룸="원룸"
    v-for="(원룸, index) in 원룸들"
    :key="index"
  />
</template>

<script>
import data from "./assets/oneroom.js";
import Discount from "./Discount.vue";
import Modal from "./Modal.vue";
import Card from "./Card.vue";

export default {
  name: "App",
  data() {
    return {
      discountNumber: 30,
      showDiscount: true,
      원룸들오리지널: [...data],
      오브젝트: { name: "kim", age: 20 },
      pushButton: 0,
      원룸들: data,
      모달창열렸니: false,
      신고수: [0, 0, 0, 0, 0, 0],
      스타일: "color:blue",
      메뉴들: ["Home", "Shop", "About"],
      products: ["역삼동원룸", "천호동원룸", "마포구원룸"],
    };
  },
  methods: {
    increase(num) {
      this.신고수[num]++;
    },
    priceSort() {
      this.원룸들.sort((a, b) => a.title.localeCompare(b.title));
    },
    sortBack() {
      this.원룸들 = [...this.원룸들오리지널];
    },
  },

  mounted() {
    setInterval(() => {
      this.discountNumber--;
    }, 1000);
  },

  components: {
    Discount,
    Modal,
    Card,
  },
};
</script>

<style>
.fade-enter-from {
  opacity: 0;
}
.fade-enter-active {
  transition: all 1s;
}
.fade-enter-to {
  opacity: 1;
}
body {
  margin: 0;
}
div {
  box-sizing: border-box;
}
.black-bg {
  width: 100%;
  height: 100%;
  background: rgba(0, 0, 0, 0.5);
  position: fixed;
  padding: 20px;
}
.white-bg {
  width: 100%;
  background: white;
  border-radius: 8px;
  padding: 20px;
}
.room-img {
  width: 100%;
  margin-top: 40px;
}
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
}
.menu {
  background: darkslateblue;
  padding: 15px;
  border-radius: 5px;
}
.menu a {
  color: white;
  padding: 10px;
}
</style>

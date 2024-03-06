<template>
  <div class="black-bg" v-if="모달창열렸니 == true">
    <div class="white-bg">
      <img :src="원룸들[pushButton].image" />
      <h4>{{ 원룸들[pushButton].title }}</h4>
      <p>{{ 원룸들[pushButton].content }}</p>
      <input v-model.number="month" />
      <p>{{ month }}개월 선택함 : {{ 원룸들[pushButton].price * month }}원</p>
      <button @click="$emit('closeModal')">닫기</button>
    </div>
  </div>
</template>
<script>
export default {
  name: "Modal",
  data() {
    return {
      month: 1,
    };
  },
  beforeUpdate() {
    if (this.month == 2) {
      alert("3개월 이상만 가능합니다.");
    }
  },

  watch: {
    month(a) {
      if (isNaN(a) == true) {
        alert("문자 입력하지 마쇼");
        this.month = 1;
      }
    },
  },
  props: {
    원룸들: Object,
    pushButton: Number,
    모달창열렸니: Boolean,
  },
};
</script>
<style></style>

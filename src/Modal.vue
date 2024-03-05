<template>
  <div class="black-bg" v-if="모달창열렸니 == true">
    <div class="white-bg">
      <h4>{{ 원룸들[pushButton].title }}</h4>
      <img :src="원룸들[pushButton].image" />
      <p>{{ 원룸들[pushButton].price }}원</p>
      <p>{{ 원룸들[pushButton].content }}</p>
      <button @click="$emit('closeModal')">닫기</button>
    </div>
  </div>
</template>
<script>
export default {
  name: "Modal",
  props: {
    원룸들: Object,
    pushButton: Number,
    모달창열렸니: Boolean,
  },
};
</script>
<style></style>

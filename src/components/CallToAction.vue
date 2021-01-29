<template>
  <section>
    <div class="content-container">
      <h3>Boost your links today</h3>
      <base-button>Get Started</base-button>
    </div>
  </section>
</template>

<script>
import BaseButton from "./BaseButton.vue";
export default {
  components: {
    BaseButton,
  },
};
</script>

<style scoped>
section {
  background: url("../assets/images/bg-boost-desktop.svg");
  background-repeat: no-repeat;
  background-size: cover;
  background-position: center;
  padding: 80px 40px;
  background-color: hsl(257, 27%, 26%);
}

section .content-container {
  margin: 0 auto;
  width: 90%;
  max-width: 600px;
  text-align: center;
}

section .content-container h3 {
  color: #fff;
  font-size: 30px;
  margin-bottom: 20px;
}

@media screen and (max-width: 416px) {
  section .content-container h3 {
    font-size: 22px;
  }
}
</style>
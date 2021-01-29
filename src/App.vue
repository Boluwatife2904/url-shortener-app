<template>
  <the-header></the-header>
  <section class="main-form">
    <statistics-section></statistics-section>
  </section>
  <call-to-action></call-to-action>
  <the-footer></the-footer>
</template>

<script>
import StatisticsSection from "./components/StatisticsSection.vue";
import CallToAction from "./components/CallToAction.vue";
import TheHeader from "./components/TheHeader.vue";
import TheFooter from "./components/TheFooter.vue";

export default {
  name: "App",
  components: {
    CallToAction,
    StatisticsSection,
    TheFooter,
    TheHeader,
  },
};
</script>

<style>
@import url("https://fonts.googleapis.com/css2?family=Poppins:wght@400;700&display=swap");
* {
  margin: 0;
  padding: 0;
  box-sizing: border-box;
}

html {
  scroll-behavior: smooth;
}

body {
  font-family: "Poppins", sans-serif;
}
</style>

<template>
  <section class="statistics-section">
    <header>
      <h3>Advanced Statistics</h3>
      <p>
        Track how your links are performing across the web with our advanced
        statistics dashboard
      </p>
    </header>
    <div class="statistics-cards">
      <statistics-card
        v-for="item in statistics"
        :key="item.title"
        :imgLink="item.imgLink"
        :title="item.title"
        :text="item.text"
      ></statistics-card>
    </div>
  </section>
</template>

<script>
import StatisticsCard from "./StatisticsCard.vue";
export default {
  components: {
    StatisticsCard,
  },
  data() {
    return {
      statistics: [
        {
          imgLink: require("../assets/images/recognition.svg"),
          title: "Brand Recognition",
          text:
            "Boost your brand recognition with each click. Generic links don't mean a thing. Branded links help instil confidence in your content. ",
        },
        {
          imgLink: require("../assets/images/records.svg"),
          title: "Detailed Records",
          text:
            "Gain insight into who is clicking your links. Knowing when and where people engage with your content helps inform better decisions.",
        },
        {
          imgLink: require("../assets/images/customizable.svg"),
          title: "Fully Customizable",
          text:
            "Improve brand awareness and content discoverability through customizable links, supercharging audience engagement.",
        },
      ],
    };
  },
};
</script>

<style scoped>
.statistics-section {
  background: hsl(230, 25%, 95%);
  padding: 120px 60px;
  overflow: hidden;
}

.statistics-section header {
  max-width: 450px;
  width: 90%;
  text-align: center;
  margin: 0 auto 100px;
}

.statistics-section header h3 {
  font-size: 26px;
  margin-bottom: 10px;
}

.statistics-section header p {
  color: hsl(257, 27%, 26%);
  line-height: 30px;
}

.statistics-section .statistics-cards {
  display: flex;
  justify-content: space-between;
  align-items: flex-start;
  flex-wrap: wrap;
}

@media screen and (max-width: 460px){
.statistics-section {
    padding: 120px 20px;
}
}
</style>
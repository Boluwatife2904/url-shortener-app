<template>
  <div class="statistics-card">
    <div class="image-container">
      <img :src="imgLink" :alt="title" />
    </div>
    <h5>{{ title }}</h5>
    <p>{{ text }}</p>
  </div>
</template>

<script>
export default {
  props: ["imgLink", "title", "text"],
};
</script>

<style scoped>
.statistics-card {
  flex: 1 0 33.3%;
  max-width: 380px;
  width: 90%;
  border-radius: 4px;
  background: #fff;
  padding: 60px 35px 40px;
  position: relative;
  z-index: 1;
}

.statistics-card:first-child::before {
  content: "";
  position: absolute;
  height: 7px;
  width: 700px;
  background: hsl(180, 66%, 49%);
  z-index: -1;
  right: -700px;
  top: 50%;
}

.statistics-section .statistics-card:nth-child(2) {
  margin-top: 40px;
}

.statistics-card:nth-child(3) {
  margin-top: 80px;
}

.statistics-card .image-container {
  position: absolute;
  background: hsl(257, 27%, 26%);
  height: 80px;
  width: 80px;
  border-radius: 50%;
  display: flex;
  justify-content: center;
  align-items: center;
  top: -40px;
}

.statistics-card .image-container img {
  height: 40px;
  width: 40px;
  display: block;
}

.statistics-card h5 {
  font-size: 20px;
  margin-bottom: 12px;
}

.statistics-card p {
  color: hsl(0, 0%, 75%);
  line-height: 30px;
  margin: 0;
}

@media screen and (max-width: 1200px) {
  .statistics-card {
    flex: 1 0 50%;
  }

  .statistics-section .statistics-card:nth-child(2),
  .statistics-section .statistics-card:nth-child(3) {
    margin-top: 0;
  }

  .statistics-card {
    margin-bottom: 70px;
  }

  .statistics-card:first-child::after {
    content: "";
    position: absolute;
    height: 200px;
    width: 7px;
    background: hsl(180, 66%, 49%);
    z-index: -1;
    left: 70px;
    top: 262px;
  }
}

@media screen and (max-width: 1200px) {
  .statistics-card:first-child::before {
    width: 400px;
    right: -400px;
  }
}

@media screen and (max-width: 902px) {
  .statistics-card {
    flex: 1 0 100%;
    text-align: center;
  }

  .statistics-card .image-container {
    left: 50%;
    transform: translateX(-50%);
  }

  .statistics-card {
    margin: 0 auto 80px;
  }

  .statistics-card:first-child::before {
    height: 500px;
    width: 7px;
    left: 50%;
    transform: translateX(-50%);
    top: 262px;
    z-index: -1;
  }

  .statistics-card:first-child::after {
    display: none;
  }
}

@media screen and (max-width: 416px) {
  .statistics-card:first-child::before {
    top: 292px;
  }
}

@media screen and (max-width: 375px) {
  .statistics-card:first-child::before {
    top: 322px;
  }
}
</style>
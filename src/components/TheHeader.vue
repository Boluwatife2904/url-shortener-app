<template>
  <section class="header-section">
    <div class="text-content">
      <h2>
        More than just <br />
        shorter links
      </h2>
      <p>
        Build your brand's recognition and get detailed insights on how your
        links are performing.
      </p>
      <base-button>Get Started</base-button>
    </div>
    <div class="image-content">
      <img src="../assets/images/working.svg" alt="" />
    </div>
  </section>
</template>

<script>
import BaseButton from "./BaseButton";
export default {
  components: {
    BaseButton,
  },
};
</script>

<style scoped>
.header-section {
  padding: 80px;
  display: flex;
  justify-content: space-between;
  align-items: center;
  overflow: hidden;
  flex-wrap: wrap;
}

.header-section .text-content,
.header-section .image-content {
  flex: 1 0 30%;
}

.header-section .text-content h2 {
  font-weight: 700;
  margin-bottom: 20px;
  font-size: 60px;
  line-height: 70px;
}

.header-section .text-content p {
  color: hsl(0, 0%, 75%);
  margin-bottom: 20px;
  font-size: 18px;
  line-height: 30px;
  width: 80%;
}

.header-section .image-content img {
  display: block;
  margin: 0 auto;
  width: 100%;
  height: 400px;
  position: relative;
  left: 100px;
  margin-bottom: 20px;
}

@media screen and (max-width: 1050px) {
  .header-section .text-content h2 {
    font-size: 50px;
  }
  .header-section .text-content p {
    font-size: 16px;
  }
}

@media screen and (max-width: 920px) {
  .header-section {
    padding: 80px 40px;
  }
}

@media screen and (max-width: 830px) {
  .header-section .image-content {
    order: 0;
  }
  .header-section .text-content {
    order: 1;
  }

  .header-section .text-content,
  .header-section .image-content {
    flex: 1 0 100%;
    text-align: center;
  }

  .header-section .image-content img {
    height: 380px;
    width: 80%;
    position: initial;
    left: 0;
  }
  .header-section .text-content p {
    width: 60%;
    margin-left: auto;
    margin-right: auto;
  }
}

@media screen and (max-width: 768px) {
  .header-section .image-content img {
    height: 300px;
  }
}

@media screen and (max-width: 680px) {
  .header-section .text-content h2 {
    font-size: 40px;
    line-height: 40px;
  }

  .header-section .text-content p {
    width: 80%;
    margin-left: auto;
    margin-right: auto;
  }
}

@media screen and (max-width: 450px) {
  .header-section .text-content h2 {
    font-size: 34px;
    line-height: 40px;
  }

  .header-section .text-content p {
    width: 100%;
  }

  .header-section .image-content img {
    width: 100%;
    height: 280px;
  }
}
</style>
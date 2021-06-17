<template>
  <section class="form-section">
    <div class="content">
      <form @submit.prevent="shortenUrl">
        <div class="form-content">
          <input
            type="url"
            v-model="link"
            :class="{ invalid: inputIsInvalid }"
            placeholder="Shorten a link here..."
            @focus="resetInputOnFocus"
          />
          <div class="spacer" v-if="inputIsInvalid"></div>
          <button type="submit">
            <span class="loader" v-if="isLoading"></span>
            <span v-else>Shorten It!</span>
          </button>
        </div>
        <p v-if="inputIsInvalid" class="error-message">Please add a link!!!</p>
      </form>

      <div class="shorten-results">
        <div v-if="errorBox" class="error-box">
          <span>&#x1F615; </span>
          <p>We have encountered an error while trying to shorten your link</p>
          <button @click="hideError">Try Again</button>
        </div>
        <shortener-result
          v-for="result in shortenedLinks"
          :key="result.shortenedLink"
          :oldLink="result.oldLink"
          :shortenedLink="result.shortenedLink"
          :copied="result.copied"
          @copy="copyShortenedLink"
        ></shortener-result>
      </div>
    </div>
  </section>
</template>

<script>
import { ref } from "vue";
import ShortenerResult from "./ShortenerResult.vue";

export default {
  components: {
    ShortenerResult,
  },
  setup() {
    // Data
    const link = ref("");
    const errorBox = ref(false);
    const inputIsInvalid = ref(false);
    const isLoading = ref(false);
    const shortenedLinks = ref([]);

    // Retrieving links from local storage
    shortenedLinks.value =
      JSON.parse(localStorage.getItem("shortenedLinks")) ||
      shortenedLinks.value;

    // Methods
    const shortenUrl = async () => {
      if (link.value.trim() === "") {
        inputIsInvalid.value = true;
      } else {
        isLoading.value = true;
        try {
          const response = await fetch(
            `https://api.shrtco.de/v2/shorten?url=${link.value.trim()}`
          );
          const responseData = await response.json();
          const newResult = {
            oldLink: responseData.result.original_link,
            shortenedLink: responseData.result.full_short_link,
            copied: false,
          };
          shortenedLinks.value.unshift(newResult);
          updateLocalStorage();
          link.value = "";
          isLoading.value = false;
        } catch {
          errorBox.value = true;
          isLoading.value = false;
        }
      }
    };

    const resetInputOnFocus = () => {
      inputIsInvalid.value = false;
      errorBox.value = false;
    };

    const hideError = () => {
      errorBox.value = false;
      link.value = "";
    };

    const copyShortenedLink = (link) => {
      const selectLink = shortenedLinks.value.find(
        (item) => item.shortenedLink === link
      );
      selectLink.copied = true;
      updateLocalStorage();
    };

    const updateLocalStorage = () => {
      localStorage.setItem(
        "shortenedLinks",
        JSON.stringify(shortenedLinks.value)
      );
    };

    return {
      link,
      errorBox,
      inputIsInvalid,
      isLoading,
      shortenedLinks,
      resetInputOnFocus,
      hideError,
      copyShortenedLink,
      shortenUrl,
    };
  },
};
</script>

<style scoped>
.loader {
  display: block;
  position: relative;
  top: 1px;
  left: 40%;
  transform: translateX(-40%);
  height: 30px;
  width: 30px;
  border-radius: 50%;
  border: 5px solid #ffffff;
  border-bottom: 5px solid hsl(180, 66%, 49%);
  animation: preloader 1s linear infinite;
}

@keyframes preloader {
  0% {
    transform: rotate(0deg);
  }
  100% {
    transform: rotate(360deg);
  }
}
/* END PRELOADER */
section {
  background: hsl(230, 25%, 95%);
}

.form-section .content {
  width: 80%;
  margin: 0 auto;
}

form {
  background: url("../assets/images/bg-shorten-desktop.svg");
  padding: 40px;
  background-repeat: no-repeat;
  background-size: cover;
  background-position: center;
  background-color: hsl(257, 27%, 26%);
  border-radius: 8px;
  top: -65px;
  position: relative;
  overflow: hidden;
}

form .form-content {
  display: flex;
  justify-content: space-between;
  align-items: flex-start;
  /* margin-bottom: 15px; */
}

form input {
  width: 100%;
  outline: none;
  background: #fff;
  border: 2px solid #fff;
  padding: 0 15px;
  margin-right: 20px;
  height: 55px;
  border-radius: 6px;
  font: inherit;
}

form input.invalid {
  border-color: hsl(0, 87%, 67%);
}

.error-message {
  color: hsl(0, 87%, 67%);
  margin: 20px 0 0;
  font-style: italic;
}

.error-box button,
form button {
  background: hsl(180, 66%, 49%);
  color: #fff;
  border-radius: 6px;
  border: 0;
  display: inline-block;
  outline: none;
  height: 55px;
  width: 150px;
  font: inherit;
  font-size: 18px;
  font-weight: 500;
  cursor: pointer;
  transition: all 0.5s ease-in-out;
}

form button:hover,
form button:focus {
  background: hsl(180, 85%, 60%);
}

form button:hover .loader,
form button:focus .loader {
  border-bottom: 5px solid hsl(180, 85%, 60%);
}

.shorten-results {
  position: relative;
  top: -45px;
}

.error-box {
  background: #fff;
  padding: 20px 40px;
  margin-bottom: 30px;
  border-radius: 6px;
  text-align: center;
  margin-bottom: 0;
}

.error-box span {
  display: block;
  font-size: 32px;
  margin-bottom: 4px;
}

.error-box p {
  color: hsl(0, 0%, 75%);
  line-height: 30px;
}

.error-box button {
  height: 40px;
  width: 120px;
  margin: 10px 0;
  font-size: 16px;
}

@media screen and (max-width: 768px) {
  .loader {
    left: 45%;
    transform: translateX(-45%);
  }
  form {
    padding: 20px;
  }

  form .form-content {
    flex-direction: column;
  }

  form input {
    margin-bottom: 15px;
  }

  form button {
    width: 100%;
  }

  .error-message {
    position: absolute;
    top: 70px;
  }

  .spacer {
    margin: 20px 0;
  }
}
</style>
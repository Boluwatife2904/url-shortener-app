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
          />
          <div class="spacer" v-if="inputIsInvalid"></div>
          <button type="submit">Shorten It!</button>
        </div>
        <p v-if="inputIsInvalid" class="error-message">Please add a link!!!</p>
      </form>

      <div class="shorten-results">
        <div class="single-result">
          <div class="original-link"><p>https://www.frontendmentor.io</p></div>
          <div class="copy-link">
            <a href="https://re.ink/k4lKyk">https://re.ink/k4lKyk</a>
            <button>Copy</button>
          </div>
        </div>
        <div class="single-result">
          <div class="original-link">
            <p>https://www.twitter.com/frontendmentor</p>
          </div>
          <div class="copy-link">
            <a href="https://re.ink/k4lKyk">https://re.ink/k4lKyk</a>
            <button>Copy</button>
          </div>
        </div>
        <div class="single-result">
          <div class="original-link">
            <p>https://www.linkedin.com/company/frontend-mentor</p>
          </div>
          <div class="copy-link">
            <a href="https://re.ink/k4lKyk">https://re.ink/k4lKyk</a>
            <button>Copy</button>
          </div>
        </div>
      </div>
    </div>
  </section>
</template>

<script>
export default {
  data() {
    return {
      link: "",
      inputIsInvalid: false,
    };
  },
  methods: {
    shortenUrl() {
      if (this.link.trim() === "") {
        this.inputIsInvalid = true;
      }
    },
  },
};
</script>

<style scoped>
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

.shorten-results {
  position: relative;
  top: -45px;
}

.single-result {
  background: #fff;
  display: flex;
  justify-content: space-between;
  align-items: center;
  /* flex-wrap: wrap; */
  border-radius: 6px;
  padding: 20px;
  margin-bottom: 15px;
  overflow: hidden;
  width: 100%;
  position: relative;
}

.single-result:last-child {
  margin-bottom: 0;
}

.single-result .original-link p {
  margin: 0;
  /* overflow: hidden;
  text-overflow: ellipsis;
  white-space: nowrap;
  width: 95%; */
}

/* .single-result .original-link,
.single-result .copy-link {
  width: 100%;
} */

.single-result .copy-link a {
  color: hsl(180, 66%, 49%);
  text-decoration: none;
  display: inline-block;
  margin-right: 15px;
}

.single-result .copy-link button {
  background: hsl(180, 66%, 49%);
  color: #fff;
  border-radius: 6px;
  border: 0;
  display: inline-block;
  outline: none;
  padding: 8px 0;
  text-align: center;
  width: 100px;
  font: inherit;
  font-size: 16px;
  font-weight: 500;
  cursor: pointer;
  transition: all 0.5s ease-in-out;
}

.copy-link button:hover,
.copy-link button:focus {
  background: hsl(180, 85%, 60%);
}

@media screen and (max-width: 768px) {
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

  .single-result {
    flex-direction: column;
    align-items: flex-start;
  }

  .single-result::after {
    content: "";
    position: absolute;
    height: 1px;
    background: hsl(0, 0%, 75%);
    width: 100%;
    top: 50px;
    left: 0;
  }

  .single-result .original-link p {
    overflow: hidden;
    text-overflow: ellipsis;
    white-space: nowrap;
    margin-bottom: 15px;
    width: 95%;
  }

  /* .copy-link{
		flex: 1 0 100%;
	} */

  /* .single-result .original-link,
  .single-result .copy-link {
    flex: 1 0 95%;
  } */

  .single-result .original-link,
  .single-result .copy-link {
    width: 100%;
  }

  .single-result .copy-link a {
    margin-bottom: 15px;
  }

  .single-result .copy-link button {
    display: block;
    width: 100%;
    text-align: center;
  }
}
</style>
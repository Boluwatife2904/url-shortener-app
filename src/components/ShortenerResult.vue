<template>
  <div class="single-result">
    <div class="original-link">
      <p>{{ oldLink }}</p>
    </div>
    <div class="copy-link">
      <a :href="shortenedLink">{{ shortenedLink }}</a>
      <button :class="{ copied: copied }" @click="copyLink" v-clipboard="shortenedLink">
        {{ copied ? "Copied!" : "Copy" }}
      </button>
    </div>
  </div>
</template>

<script>
export default {
  props: ["oldLink", "shortenedLink", "copied"],
  setup(props, context) {
    const copyLink = () => {
      context.emit("copy", props.shortenedLink)
    }
    return {
      copyLink 
    }
  }
};
</script>

<style scoped>
.single-result {
  background: #fff;
  display: flex;
  justify-content: space-between;
  align-items: center;
  border-radius: 6px;
  padding: 20px;
  margin-top: 20px;
  overflow: hidden;
  width: 100%;
  position: relative;
}

.single-result:last-child {
  margin-bottom: 0;
}

.single-result .original-link p {
  margin: 0;
}

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

.single-result .copy-link button.copied {
  background-color: hsl(257, 27%, 26%);
}

.copy-link button:hover,
.copy-link button:focus {
  background: hsl(180, 85%, 60%);
}

@media screen and (max-width: 768px) {
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
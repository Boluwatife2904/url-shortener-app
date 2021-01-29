<template>
  <button>
    <slot></slot>
  </button>
</template>

<script>
export default {};
</script>

<style scoped>
button {
  background: hsl(180, 66%, 49%);
  color: #fff;
  border-radius: 30px;
  border: 0;
  display: inline-block;
  outline: none;
  padding: 12px 30px;
  font: inherit;
  font-size: 18px;
  font-weight: 500;
  cursor: pointer;
  transition: all .5s ease-in-out;
}

button:hover,
button:focus{
  background: hsl(180, 85%, 60%);
}

</style>
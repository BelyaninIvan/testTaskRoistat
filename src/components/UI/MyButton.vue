<template>
  <button
    :type="buttonType"
    @click="$emit('click')"
    class="button"
  >
    <slot></slot>
  </button>
</template>
<script>
export default {
  name: 'my-button',
  props: {
    buttonType: {
      type: String,
      default: 'button',
    }
  }
}
</script>
<style scoped>
  .button {
    margin: 0;
    padding: 15px;
    border: none;
    background-color: rgba(134, 209, 119, 0.753);
    border-radius: 10px;
    font-weight: 700;
    font-size: 20px;
    color: white;
    transition: all ease-in 0.7s;
  }

  .button:hover {
    opacity: .7;
    cursor: pointer;
  }
</style>
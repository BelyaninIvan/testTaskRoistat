<template >
  <input
    :type="typeInput"
    :minlength="minLength"
    :maxlength="maxLength"
    :required="required"
    :value="value"
    @input="updateInput"
    class="input"
  >
</template>
<script>
export default {
  name: 'my-input',
  props: {
    value: {
      type: String,
      default: null,
    },
    typeInput: {
      type: String,
      default: null,
    },
    minLength: {
      type: String,
      default: null,
    },
    maxLength: {
      type: String,
      default: null,
    },
    required: {
      type: Boolean,
      default: true,
    },
  },
  methods: {
    updateInput(event) {
      this.$emit('input', event.target.value);
    },
  },
}
</script>
<style scoped>
  .input {
    margin: 0;
    padding: 0;
    border: 0;
    outline: none;
    padding: 10px 15px;
    background-color: rgba(134, 209, 119, 0.753);
    border-radius: 10px;
    font-size: 20px;
    font-weight: 700;
    color: white;
  }

.input::placeholder {
    color: rgb(255, 255, 255);
    opacity: .6;
  }
</style>
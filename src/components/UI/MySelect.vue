<template>
  <select 
    class="select" 
    :value="value"
    @change="changeOption"
  >
    <option class="select__option" value="">Пусто</option>
    <select-option
      v-for="option in options"
      :key="option.id"
      :value="option.id"
      :option-item="option"
      class="select__option"
    >
      {{ option.name }}
    </select-option>
  </select>
</template>
<script>
import SelectOption from '../SelectOption.vue';
export default {
  name: 'my-select',
  components: {
    SelectOption
  },
  props: {
    value: {
      type: String,
      default: null,
    },
    options: {
      type: Array,
      default: () => [],
    }
  },
  methods: {
    changeOption(event) {
      this.$emit('input', event.target.value);
    },
  },
}
</script>
<style scoped>
  .select {
    margin: 0;
    padding: 0;
    border: 0;
    outline: none;

    padding: 15px 20px;
    background-color: rgba(134, 209, 119, 0.753);
    border-radius: 10px;

    font-size: 20px;
    font-weight: 700;
    color: rgb(255, 255, 255);
  }

  .select:hover {
    cursor: pointer;
  }
</style>
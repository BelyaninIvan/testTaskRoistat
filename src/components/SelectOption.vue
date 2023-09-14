<template>
  <option
    :value="optionItem.id"
    class="select__option"
  >
    {{ optionItem.name }}
  </option>
    <!-- <select-option
        v-for="chOption in optionItem.children"
        :option-item="chOption"
        :value="chOption.id"
    >
    {{ chOption.name }}
    </select-option> -->
    
</template>
<script>
export default {
  name: 'select-option',
  props: {
    optionItem: {
      type: Object,
      default: null,
    },
    value: {
      type: Number,
      default: null,
    }
  },
}
</script>
<style scoped>
  .select__option {
    font-family: 'Avenir', Helvetica, Arial, sans-serif;
    color: rgb(99, 92, 92);
  }
</style>
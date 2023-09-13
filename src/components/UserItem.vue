<template>
  <li class="table__row">
    <p
      @click="toggle"
      @dblclick="changeType"
      :class="{ bold: isFolder }"
      class="table__row-elem"
    >
      {{ model.name }}
      <span v-if="isFolder">
        {{ isOpen ? '-' : '+' }}
      </span>
    </p>
    <p class="table__row-elem">
      {{ model.tel }}
    </p>
    <ul v-show="isOpen" v-if="isFolder" class="table table_type_next">
      <user-item
        v-for="item in model.children"
        :model="item"
      >
      </user-item>
    </ul>
  </li>
</template>
<script>
export default {
  name: 'user-item',
  data() {
    return {
      isOpen: false,
    }
  },  
  props: {
    model: {
      type: Object,
      default: null,
    },
  },
  computed: {
    isFolder() {
      return this.model.children && this.model.children.length;
    },
  },
  methods: {
    toggle() {
      if (this.isFolder) {
        this.isOpen = !this.isOpen
      }
    },
    changeType() {
      if (!this.isFolder) {
        this.model.children = [];
        this.addChild();
        this.isOpen = true;
      }
    },
  },
}
</script>
<style scoped>
  .table_type_next {
    margin-top: 0;
    margin-left: 30px;
    padding: 0;
  }
</style>
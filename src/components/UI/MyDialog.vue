<template >
  <div
    v-if="show === true"
    @click.stop="hideDialog" 
    class="modal" 
  >
    <div 
      @click.stop 
      class="modal__content"
    >
      <h2 class="modal__title">
        {{ modalTitle }}
      </h2>

      <slot></slot>
    </div>
  </div>
</template>
<script>
export default {
  name: 'my-dialog',
  props: {
    show: {
      type: Boolean,
      default: false,
    },
    modalTitle: {
        type: String,
        default: null,
    },
  },
  methods: {
    hideDialog() {
      this.$emit('update:show', false);
    },
  },
}
</script>
<style scoped>
  .modal {
    top: 0;
    bottom: 0;
    right: 0;
    left: 0;
    background-color: rgba(0, 0, 0, 0.4);
    position: fixed;
    display: flex;
  }

  .modal__title {
    margin: 0;
    margin-bottom: 25px;
    color: white;
    text-align: center;
    font-weight: 900;
  }

  .modal__content {
    margin: auto;
    background-color: rgb(185, 180, 132);
    border-radius: 20px;
    padding: 25px;
  }
</style>
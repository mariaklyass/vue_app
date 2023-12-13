<template>
  <div class="modal" v-if="show" @click="hideModal">
    <div @click.stop class="modal__content">
      <slot></slot>
    </div>
  </div>
</template>

<script>
export default {
  props: {
    show: {
      type: Boolean,
      default: false,
    },
  },
  methods: {
    hideModal() {
      this.$emit("update:show", false);
    },
  },
};
</script>

<style scoped>
.modal {
  z-index: 9999;
  position: fixed;
  top: 0;
  bottom: 0;
  right: 0;
  left: 0;
  display: flex;
  background-color: rgba(0, 0, 0, 0.7);
}
.modal__content {
  margin: auto;
  padding: 20px;
  background-color: rgba(255, 249, 249, 0.95);
  border-radius: 12px;
  min-height: 50px;
  min-width: 300px;
}
</style>

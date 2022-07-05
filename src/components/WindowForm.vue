<template>
  <div class="window" v-if="show" @click.stop="hideWindow">
    <div @click.stop class="window__content">
      <slot></slot>
    </div>
  </div>
</template>

<script>
export default {
  name: 'window-form',
  props: {
    show: {
      type: Boolean,
      default: false
    }
  },
  methods: {
    hideWindow() {
      this.$emit('update:show', false)
    }
  }
}
</script>

<style>
.window {
  top: 0;
  bottom: 0;
  right: 0;
  left: 0;
  background: rgba(0, 0, 0, 0.5);
  position: fixed;
  display: flex;
}

.window__content {
  margin: auto;
  background: white;
  border-radius: 12px;
  min-height: 50px;
  max-height: 500px;
  padding: 20px;
}
</style>
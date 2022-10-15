<template>
  <teleport to="body">
    <transition name="fade">
      <div class="modal-wrapper" v-if="modalstate">
        <div
          class="modal-background"
          @click="$emit('update:modalstate', false)"
        />
        <div class="modal-container">
          <div class="closeModal"></div>
        </div>
      </div>
    </transition>
  </teleport>
</template>

<script>
export default {
  name: "Modal",
  props: {
    modalstate: Boolean,
  },
};
</script>

<style scoped>
.modal-wrapper {
  position: absolute;
  top: 0;
  left: 0;
  width: 100%;
  height: 100%;
  display: flex;
  justify-content: center;
  align-items: center;
}
.modal-background {
  position: absolute;
  top: 0;
  left: 0;
  z-index: 3;
  width: 100%;
  height: 100%;
  background: rgb(0, 0, 0, 0.5);
}
.modal-container {
  box-sizing: border-box;
  position: relative;
  z-index: 4;
  width: 200px;
  height: 150px;
  background: white;
}
.fade-enter-active,
.fade-leave-active {
  transition: opacity 0.5s ease;
}

.fade-enter-from,
.fade-leave-to {
  opacity: 0;
}
</style>


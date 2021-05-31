<template>
  <div class="home">
    <transition name="toast"> <Toast v-if="showToast" /> </transition>
    <Todos @badValue="triggerToast" />
  </div>

  <transition name="fade">
    <p v-if="pTrue">First transition component</p>
  </transition>

  <button @click="pTrue = !pTrue">Toggle P</button>
</template>

<script>
import { ref } from "vue";
import Toast from "../components/Toast";
import Todos from "../components/Todos";

export default {
  components: { Toast, Todos },
  setup() {
    const showToast = ref(false);

    const pTrue = ref(false);

    const triggerToast = () => {
      showToast.value = true;
      setTimeout(() => (showToast.value = false), 3000);
    };

    return { showToast, triggerToast, pTrue };
  },
};
</script>

<style>
.toast-enter-from {
  opacity: 0;
  transform: translateY(-60px);
}
.toast-enter-to {
  opacity: 1;
  transform: translateY(0);
}
.toast-enter-active {
  transition: all 0.3s ease;
}
.toast-leave-from {
  opacity: 1;
  transform: translateY(0);
}
.toast-leave-to {
  opacity: 0;
  transform: translateY(-60px);
}
.toast-leave-active {
  transition: all 0.3s ease;
}
</style>

<template>
  <div class="home">
    <Toast v-if="showToast" />
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
.fade-enter-from {
  opacity: 0;
}
.fade-enter-to {
  opacity: 1;
}
.fade-enter-active {
  transition: all 1s ease;
}
.fade-leave-from {
  opacity: 1;
}
.fade-leave-to {
  opacity: 0;
}
.fade-leave-active {
  transition: all 1s ease;
}
</style>

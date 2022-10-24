<template>
  <button @click="open = true">On Click Out Side in Vue Use </button>
  <div class="popup" v-if="open">
    <div class="popup-content" ref="popup">
      <button class="button absolute " title="Close" @click="open = false">
        𝖷
      </button>
      Lắng nghe các nhấp chuột bên ngoài một phần tử. Hữu ích cho phương thức hoặc trình đơn thả xuống.
    </div>
  </div>
</template>
<script lang="ts" setup >
import { ref } from 'vue'
import { onClickOutside } from '@vueuse/core'
const open = ref(false) // state of our popup
const popup = ref() // template ref
// whenever our popup exists, and we click anything BUT it
onClickOutside(popup, () => {
  open.value = false
})
</script>
<style scoped>
button {
  cursor: pointer;
  border: none;
  outline: none;
  background-color: #2ecc71;
  color: white;
  padding: 5px 10px;
}

.popup {
  position: fixed;
  top: 0;
  left: 0;
  width: 100vw;
  height: 100vh;
  display: flex;
  align-items: center;
  justify-content: center;
  background: #1209098a;
}

.button {
  right: 41.1rem;
  bottom: 30.5rem
}

.popup-content {
  width: 500px;
  padding: 20px;
  width: 30%;
  background: #fff;
}
</style>  
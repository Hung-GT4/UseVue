<template>
      <!--div to display the sprite in-->
      <div class="sprite" :style="{ 'background-position': activePosition + 'px' + '50 %' }"></div>
</template>

<style>
.sprite {
      /* display the image*/
      background: url(https://freesvg.org/img/1525205509.png) no-repeat;

      /* each frame is 75px wide so limit container to display one at a time */
      width: 75px;

      /* main is roughly 150px tall */
      height: 150px;

      /* the image has some space on top and bottom so this accounts for that */
      /*Step 1*/
      background-position: 0px 50%;
      /*Step 2*/
      /* background-position: -75px 50%;
      /*Step 3*/
      /* background-position: -150px 50%; */
      /*Step 4*/
      /* background-position: -225px 50%; */

}
</style>
<script setup lang="ts">
import { useIntervalFn } from '@vueuse/core';
import { ref } from "vue";
const activePosition = ref(0);
useIntervalFn(() => {
      if (activePosition.value > -525) {
            activePosition.value -= 75;
      }
      else {
            activePosition.value = 0;
      }
}, 200);
</script>
 
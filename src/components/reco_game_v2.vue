<template>
  <div class="pore d-flex p-2 justify-content-end align-items-end">
    <div class="zi-1 fol">
      <p class="f-12 text-light fw-bold zi-1">
        {{ tittle }}
      </p>
      <div class="fow justify-content-end gap-1">
        <p style="color: #405c9a" class="f-8"> </p>
      </div>
    </div>
    <!--<div :style="{'background-image': `url(${props.image})`}" style="border-bottom: 3px solid #2ac2dd" class="dark posa top-left full rounded-2"></div>-->
    <UseImage :src="props.image" class="dark posa top-left full rounded-2">
      <template #loading>
        <div class="force-center posa top-left full rounded-2">
          <img width=56 src="assets/load.svg" alt="">
        </div>
      </template>
    </UseImage>
  </div>
</template>
<!-- -->

<script setup>
  import {UseImage} from '@vueuse/components'
  const props = defineProps(["tittle", "genre", "image"])
</script>
<!-- -->

<style scoped></style>

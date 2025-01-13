<template>
    <div style="height: 100px" class="gap-1  fow pore">
        <div :style="{'background-image': `url(${props.image})`}" style="min-height:100px; aspect-ratio:1/1" class="bg-img rounded-2"></div>
        <div class="rounded-1 h-100 fol  text-light jen px-2">
            <p class="fw-18 fw-bold">{{tittle}}</p>
            <p style="width: 90%" class="fw-8 f-12 overflow-scroll">{{desc}}</p>
        </div>
        <div style="background-color: #363b59; right: 4px; bottom: 4px" class="rounded-1 p-1 fow posa gap-1">
            <img width="12" src="assets/el_windows.svg" alt="" />
            <p style="color: #6aa1fe" class="f-8">PC</p>
        </div>
    </div>
</template>
<!-- -->

<script setup>
  const props= defineProps(['tittle', 'desc', 'image' ])
</script>
<!-- -->

<style scoped></style>

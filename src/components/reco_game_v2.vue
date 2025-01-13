<template>
  <div class=" pore d-flex p-2 justify-content-end align-items-end">
    <div class="zi-1 fol">
      <p class="f-12 text-light fw-bold zi-1">
        {{tittle}}
      </p>
      <div class="fow justify-content-end gap-1 ">
        <p style="color:#405C9A" class="f-8">
        
        </p>
      </div>
    </div>
    <div :style="{'background-image' : `url(${props.image})`}" style="border-bottom: 3px solid #2AC2DD" class="dark posa top-left full bg-warning rounded-2  "></div>
  </div>

</template>
<!-- -->

<script setup>
  const props= defineProps(['tittle', 'genre', 'image'])
</script>
<!-- -->

<style scoped>
</style>
<template>
  <div style="width: 100%; height: 100%" class="text-light pore rounded-2 d-flex justify-content-end align-items-end p-2">
    <p style="top:0; left:0" class="posa f-12 text-light p-1 zi-1">
      {{dev}}
    </p>
    <div style="left: -7px; top:0px; width: 4px; background-color: #555F95" class="posa rounded-2 h-100 zi-1"></div>
    <div class="pore zi-1">
      <p style="text-align: right" class="fw-bold f-18">
        {{tittle}}
      </p>
      <p style="text-align: right" class="f-8">
        {{desc}}
      </p>
      <div class="my-2"></div>
      <div class="f-8 fw-bold fow justify-content-end alen gap-2">
        <div style="background-color: #363B59" class="rounded-1 p-1 fow gap-1">
          <img width=12 src="assets/el_windows.svg" alt="">
          <p style="color: #6AA1FE">
            {{platform}}
          </p>
        </div>
        <div class="fow  gap-1">
          <img width=12 src="assets/el_tag.svg" alt="">
          <p style="color: white">
            {{genre}}
          </p>
        </div>


      </div>
    </div>

    <div :style="{'background-image':`url(${props.image})`}" style="z-index: 0" class="rounded-2 posa full bg-img top-left z-0 dark">

    </div>

  </div>

</template>
<!-- -->

<script setup>
  const props= defineProps([
  'image',
  'tittle',
  'desc',
  'platform',
  'genre',
  'dev'
  ])
</script>
<!-- -->

<style scoped>
</style>
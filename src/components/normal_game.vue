<template>
  <div style="width: 200px; aspect-ratio: 200/180; background-color: #272a3b" class="main rounded-2 text-light gap-1 p-1 alen fol" tabindex="1">
    <div class="flex-grow-1 pore w-100">
      <div data-image style="height: 122%; transition: all 500ms ease" class="w-100 top-left posa fol alen gap-1">
        <!--<div :style="{'background-image': `url(${props.image})`}" class="bg-img flex-grow-1 w-100"></div>-->
        <UseImage style="object-fit: cover" class="w-100 h-100 overflow-hidden" :src="props.image">
          <template #loading>
            <div class="force-center flex-grow-1">
              <img width="56" src="assets/load.svg" alt="" />
            </div>
          </template>
        </UseImage>
        <p data-tittle style="background-color: #363b59" class="w-100 text-center rounded-2 fw-bold f-12 p-1">
          {{ tittle }}
        </p>
      </div>
    </div>
    <div data-info style="color: #a6a6a6; opacity: 0; transition: all 500ms ease" class="alen fol gap-1 f-8">
      <div class="fow gap-1">
        <img width="10" src="assets/el_tag.svg" alt="" />
        <p>
          {{ genre }}
        </p>
      </div>
      <div class="fow gap-1">
        <img width="10" src="assets/el_windows.svg" alt="" />
        <p>
          {{ dev }}
        </p>
      </div>
    </div>
    <div data-line class="w-100 rounded-3"></div>
  </div>
</template>
<!-- -->

<script setup>
  import {UseImage} from "@vueuse/components"
  const props = defineProps(["tittle", "dev", "genre", "image"])
</script>
<!-- -->

<style scoped>
  .main:focus [data-image] {
    height: 100% !important;
  }
  .main:focus [data-info] {
    opacity: 1 !important;
  }

  [data-tittle] {
    color: #a5a5a5;
  }
  .main:focus [data-tittle] {
    color: #6aa1fe;
  }

  [data-line] {
    border: 1px solid #535f9b;
  }

  .main:focus [data-line] {
    border: 1px solid #6aa1fe;
  }

  @media screen and (max-width: 576px) {
    .main {
      width: 160px !important;
    }
    [data-image] {
      height: 130% !important;
    }
  }
</style>

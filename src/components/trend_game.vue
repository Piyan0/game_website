<template>
  <div main tabIndex="1" style="width: 200px; aspect-ratio: 200/180" class="fol alen pore">
    <div class="posa top_left full fow force-center z-0">
      <img style="top: -10px" width="210" src="assets/el_blur.svg" class="blur pore" alt="" />
    </div>
    <div data-border style="border: 4px solid #424c83; border-bottom: 8px solid #424c83; border-radius: 10px" class="w-100 overflow-hidden flex-grow-1 zoom-wrapper">
      <UseImage data-image style="transition: transform 500ms" class="pore z-1 full" :src="props.image">
        <template #loading>
          <div class="force-center full">
            <img width=56 src="assets/load.svg" alt="">
          </div>
        </template>
      </UseImage>
    </div>
    <div style="color: #699ff7" class="w-100 fow jen alen gap-1 my-2 pore z-1">
      <p style="" class="f-12 text-center overflow-hidden">
        <span> <img style="top: -1px" class="pore" width="12" src="assets/fire.svg" alt="" /> </span>&nbsp{{ tittle }}
      </p>
    </div>
  </div>
</template>
<!-- -->

<script setup>
  import {UseImage} from "@vueuse/components"
  const props = defineProps(["tittle", "image"])
</script>
<!-- -->

<style scoped>
  .blur {
    filter: brightness(0) saturate(100%) invert(53%) sepia(66%) saturate(951%) hue-rotate(195deg) brightness(103%) contrast(101%);
  }

  [main]:focus [data-image] {
    transform: scale(1.2);
  }
  [main]:focus [data-border] {
    border: 4px solid #699ff7 !important;
    border-bottom: 8px solid #699ff7 !important;
  }
  @media screen and (max-width: 567px) {
    [main] {
      width: 160px !important;
    }
  }
</style>

<script setup>

import AppButton from "@/components/AppButton.vue";
import IconClose from "@/components/icons/IconClose.vue";

const model = defineModel()
</script>

<template>
  <teleport to="body">
    <div v-if="model" class="bg" @click="model = false" />
    <transition>
      <div class="modal" v-if="model">
        <icon-close class="close" @click="model = false" />
        <img src="/modal-img.jpg" alt="img">
        <div class="text">
          <p class="title">Profit goes to SWEN</p>
          <p class="description">By leaving a tip, you take care of nature</p>
        </div>
        <app-button title="Learn more about SWEN"/>
      </div>
    </transition>
  </teleport>
</template>

<style scoped lang="scss">
.v-enter-active,
.v-leave-active {
  transition: opacity 0.5s ease;
}

.v-enter-from,
.v-leave-to {
  opacity: 0;
}

.bg{
  background: var(--color-black);
  opacity: 0.5;
  position: fixed;
  top: 0;
  left: 0;
  bottom: 0;
  right: 0;
  z-index: 1000;
}

.modal{
  max-width: 320px;
  width: 100%;
  background: var(--color-white);
  position: absolute;
  top: 50%;
  left: 50%;
  transform: translate(-50%, -50%);
  padding: 12px;
  border-radius: 24px;
  z-index: 1100;

  .close {
    position: absolute;
    top: 20px;
    right: 20px;
    padding: 4px;
    border-radius: 100px;
    background: var(--color-white);
  }

  img{
    width: 100%;
  }

  .text{
    margin: 16px 0;

    .title{
      text-align: center;
      font-size: 18px;
      line-height: 24px;
      font-weight: 500;
      color: var(--color-black-26);
      margin-bottom: 8px;
    }

    .description{
      text-align: center;
      font-size: 17px;
      line-height: 24px;
      font-weight: 400;
      color: var(--color-gray-80);
    }
  }
}
</style>

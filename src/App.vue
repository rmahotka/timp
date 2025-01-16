<script setup>

import AppHeader from "@/components/AppHeader.vue";
import HeaderCarousel from "@/components/HeaderCarousel.vue";
import AppPersonnel from "@/components/AppPersonnel.vue";
import AppTips from "@/components/AppTips.vue";
import FromRate from "@/components/FromRate.vue";
import AppDidYouLike from "@/components/AppDidYouLike.vue";
import FormAmount from "@/components/FormAmount.vue";
import AppTextArea from "@/components/AppTextArea.vue";
import {ref, watch} from "vue";
import AppFooter from "@/components/AppFooter.vue";
import AppModelInfo from "@/components/AppModelInfo.vue";

const textarea = ref('')
const checkTips  = ref(false)
const amount = ref(0)
const rateExperience = ref(0)
const rateService = ref(0)

const openModal = ref(false)

watch(openModal,()=>{
  const body = document.querySelector("body")
  openModal.value ? body.style.overflow="hidden" : body.style.overflow="auto"

})

</script>

<template>
  <app-model-info v-model="openModal"/>

  <app-header />
  <header-carousel @click="openModal = true"/>
  <app-personnel />
  <section class="form">
    <div class="container">
      <form-amount v-model="amount"/>
      <from-rate title="Rate your experience" v-model="rateExperience"/>
      <from-rate v-if="rateExperience" title="Rate Service" v-model="rateService"/>
      <app-did-you-like  v-if="rateExperience"/>
      <app-text-area  v-if="rateExperience" title="Share your fedback" placeholder="Describe your own" v-model="textarea"/>
      <app-tips v-model="checkTips" />
    </div>
  </section>
  <AppFooter v-model="amount"/>
</template>

<style scoped>
</style>

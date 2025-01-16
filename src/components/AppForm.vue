<script setup>
import {ref} from "vue";
import FormAmount from "@/components/FormAmount.vue";
import FromRate from "@/components/FromRate.vue";
import AppDidYouLike from "@/components/AppDidYouLike.vue";
import AppTextArea from "@/components/AppTextArea.vue";
import AppTips from "@/components/AppTips.vue";

const textarea = ref('')
const checkTips  = ref(false)
</script>

<template>
  <section class="form">
    <div class="container">
      <form-amount />
      <from-rate title="Rate your experience" />
      <from-rate title="Rate Service" />
      <app-did-you-like />
      <app-text-area title="Share your fedback" placeholder="Describe your own" v-model="textarea"/>
      <app-tips v-model="checkTips" />
    </div>
  </section>
</template>

<style scoped lang="scss">

</style>

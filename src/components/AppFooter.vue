<script setup>

import AppButton from "@/components/AppButton.vue";
import IconApplePay from "@/components/icons/IconApplePay.vue";

const modelAmount = defineModel()
</script>

<template>
<footer class="footer">
  <div class="footer-block">
    <div class="footer-block-pay">
      <span class="footer-block-pay--left">To pay {{modelAmount}}€</span>
      <span class="footer-block-pay--right">Service fees {{modelAmount? modelAmount * 1.2/100 : 0}}€ </span>
    </div>
    <div class="footer-block-btn">
      <app-button title="Pay with" :icon="IconApplePay"/>
      <app-button title="Pay with debit card" color="purple"/>
    </div>
    <div class="footer-block-info">
      By clicking the button, you agree to our <span>Terms of Use</span> and <span>Privacy Policy</span>,
      and <span>authorize payment</span> and <span>data processing</span>.
    </div>
  </div>
</footer>
</template>

<style scoped lang="scss">
.footer {
  position: fixed;
  bottom: 0;
  left: 0;
  right: 0;
  background: var(--color-white);
  border-radius: 20px 20px 0 0;
  padding: 24px 20px 11px 20px;

  &-block{
    &-pay{
      display: flex;
      align-items: center;
      justify-content: space-between;
      padding-bottom: 12px;
      margin-bottom: 12px;
      border-bottom: 1px solid #F3F3F3;

      &--left{
        font-size: 15px;
        line-height: 24px;
        font-weight: 500;
        color: var(--color-black);
      }

      &--right{
        font-size: 14px;
        line-height: 20px;
        font-weight: 500;
        color: var(--color-gray-80);
      }
    }

    &-btn{
      display: flex;
      flex-direction: column;
      align-items: center;
      gap: 8px;
      margin-bottom: 12px;
    }

    &-info{
      font-size: 11px;
      line-height: 15px;
      font-weight: 500;
      text-align: center;
      color: var(--color-gray-80);

      span{
        color: var(--color-purple);
      }
    }
  }
}
</style>

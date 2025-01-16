<script setup>

import Logo from "@/components/icons/Logo.vue";
import AngleDown from "@/components/icons/AngleDown.vue";
</script>

<template>
  <header class="header">
    <div class="container">
      <div class="block">
        <Logo class="logo"/>
        <div class="lang">
          <span>En</span>
          <angle-down class="lang-svg"/>
        </div>
      </div>
    </div>
  </header>
</template>

<style scoped lang="scss">
.header{
  max-width: 1000px;
  margin: 0 auto;
  background: var(--color-white);
  padding: 12px 0;

  .block{
    display: flex;
    align-items: center;
    justify-content: flex-end;
  }

  .logo{
    position: absolute;
    left: 50%;
    transform: translateX(-50%);
  }

  .lang{
    display: flex;
    align-items: center;
    gap: 4px;
    cursor: pointer;

    span{
      color: var(--color-black-0f);
      font-size: 16px;
      line-height: 24px;
      font-weight: 500;
    }

    &-svg{
      color: var(--color-purple);
    }
  }
}
</style>

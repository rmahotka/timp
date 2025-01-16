<script setup>

import AbstractionIcon from "@/components/icons/AbstractionIcon.vue";

import { onMounted } from 'vue'

function addAnimation() {
  const scrollerInner = document.querySelector('.animate')
  const scrollerContent = Array.from(scrollerInner.children)

  scrollerContent.forEach(item => {
    const duplicatedItem = item.cloneNode(true)
    duplicatedItem.setAttribute('aria-hidden', true)
    scrollerInner.appendChild(duplicatedItem)
  })
}

onMounted(() => {
  if (!window.matchMedia('(prefers-reduced-motion: reduce)').matches) {
    addAnimation()
  }
})
</script>

<template>
  <div class="block">
    <div class="animate">
      <abstraction-icon class="svg"/>
      <span>Part of the profit goes to sWen</span>
      <abstraction-icon class="svg"/>
      <span>By leaving a tip, you take care of nature</span>
      <abstraction-icon class="svg"/>
      <span>Part of the profit goes to sWen</span>
      <abstraction-icon class="svg"/>
      <span>By leaving a tip, you take care of nature</span>
      <abstraction-icon class="svg"/>
      <span>Part of the profit goes to sWen</span>
      <abstraction-icon class="svg"/>
      <span>By leaving a tip, you take care of nature</span>
    </div>
  </div>
</template>

<style scoped lang="scss">
.block{
  max-width: 1000px;
  margin: 0 auto;
  padding: 10px 0;
  overflow: hidden;
  background: rgb(245,207,200);
  background: linear-gradient(90deg, rgba(245,207,200,1) 15%, rgba(197,237,248,1) 57%, rgba(221,254,213,0.86) 96%);

  .animate{
    display: flex;
    align-items: center;
    flex-wrap: nowrap;
    gap: 8px;
    width: max-content;
    animation: scroll 10s forwards linear infinite;

    .svg{
      flex: 1 0 auto;
    }
  }

  span{
    font-family: "Montserrat", serif;
    font-size: 12px;
    line-height: 20px;
    font-weight: 600;
    text-transform: uppercase;
    white-space: nowrap;
    color: var(--color-black-0f);
    text-shadow: 0 4px 4px #00000040;
  }
}

@keyframes scroll {
  to {
    transform: translate(calc(-50% - 0.3rem));
  }
}
</style>

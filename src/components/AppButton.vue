<script setup>
defineProps({
  title:{
    type: String,
    default: ''
  },
  icon:{
    type: [Object],
    default: ()=> {}
  },
  color: {
    type: String,
    default: 'dark'
  }
})


</script>

<template>
  <button class="btn" :class="color">
    {{title}}
    <component v-if="icon" :is="icon" />
  </button>
</template>

<style scoped lang="scss">
.btn{
  border: 0;
  display: flex;
  align-items: center;
  justify-content: center;
  gap: 10px;
  width: 100%;
  color: var(--color-white);
  font-size: 16px;
  line-height: 24px;
  font-weight: 500;
  padding: 10px;
  border-radius: 40px;
}

.dark{
  background: var(--color-black-0f);
}

.purple {
  background: var(--color-purple);
}
</style>

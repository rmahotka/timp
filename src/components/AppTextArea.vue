<script setup>
defineProps({
  title:{
    type: String,
    default: ''
  },
  placeholder:{
    type: String,
    default: ''
  }
})

const model = defineModel()
</script>

<template>
<div class="textarea">
  <p class="title">{{title}}</p>
  <div class="textarea-block">
    <textarea :placeholder="placeholder" v-model="model"/>
  </div>
</div>
</template>

<style scoped lang="scss">
.textarea{
  margin-bottom: 16px;

  .title{
    font-size: 15px;
    line-height: 24px;
    font-weight: 500;
    color: var(--color-black);
    margin-bottom: 12px;
    text-align: center;
  }

  &-block{
    padding: 20px;
    background: var(--color-white);
    border-radius: 20px;

    textarea{
      width: 100%;
      height: 65px;
      border: 0;
      padding: 0;
      color: var(--color-black);
      font-size: 17px;
      line-height: 24px;
      font-weight: 400;

      &:focus-visible{
        outline: 0;
      }

      &::placeholder{
        color: var(--color-gray-80);
      }
    }
  }
}
</style>

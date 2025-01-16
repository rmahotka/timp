<script setup>
import StarIcon from "@/components/icons/StarIcon.vue";

defineProps({
  title:{
    type: String,
    default: ''
  }
})

const model = defineModel()

const setRating = (index) => {
  model.value = index ;
};
</script>

<template>
<div class="rate">
  <p class="rate-title">{{title}}</p>
  <div class="rate-block">
    <star-icon
        v-for="(star, index) in 5"
        :key="index"
        class="star"
        :class="{ 'star-active': index < model }"
        @click="setRating(star)"
    />
  </div>
</div>
</template>

<style scoped lang="scss">
.rate{
  margin-bottom: 16px;

  &-title{
    position: relative;
    font-size: 15px;
    line-height: 24px;
    font-weight: 500;
    color: var(--color-black-0f);
    margin-bottom: 12px;
    text-align: center;
    overflow: hidden;
    background: var(--colot-body);

    &:after{
      background: var(--color-purple);
      position: absolute;
      top: 50%;
      left: 100%;
      transform: translate(-50%, 50%);
      content: "";
      display: block;
      height: 1px;
      width: 50%;
    }

    &:before{
      background: var(--color-purple);
      position: absolute;
      top: 50%;
      left: 0;
      transform: translate(-50%, 0);
      content: "";
      display: block;
      height: 1px;
      width: 50%;
    }
  }

  &-block{
    background: var(--color-white);
    padding: 16px;
    border-radius: 20px;
    display: flex;
    align-items: center;
    justify-content: center;
    gap: 16px;

    .star{
      color: var(--color-gray);

      &-active{
        color: var(--color-purple);
      }
    }
  }
}
</style>

<script setup>

import AbstractionDidLike from "@/components/icons/AbstractionDidLike.vue";
import {ref} from "vue";

const btnList = ref([
  {id: 1, icon: 'Smiling-face-with-hearts.png', title:'Service'},
  {id: 2, icon: 'Glowing-star.png', title:'Cleanliness'},
  {id: 3, icon: 'Smiling-face.png', title:'Atmosphere'},
  {id: 4, icon: 'Hamburger.png', title:'Food quality'},
])

const activeBtn = ref([])

const onActiveBtn = (id) => {
  const index = activeBtn.value.indexOf(id);
  if (index !== -1) {
    activeBtn.value.splice(index, 1);
  } else {
    activeBtn.value.push(id);
  }
};
</script>

<template>
<section class="did-like">
    <p class="title">What did you like?</p>
    <div class="block">
      <div v-for="btn in btnList"
           :key="btn.id"
           @click="onActiveBtn(btn.id)"
           class="block-btn"
          :class="{'block-btn-active': activeBtn.includes(btn.id)}"
      >
        <button class="btn" >
          <abstraction-did-like class="svg"/>
          <img :src="btn.icon" alt="smile" :class="{'hamburger':btn.id === 4}">
        </button>
        <p class="block-btn-title">{{btn.title}}</p>
      </div>
    </div>
</section>
</template>

<style scoped lang="scss">
.did-like{
  margin-bottom: 16px;
  .title{
    font-size: 15px;
    line-height: 24px;
    font-weight: 500;
    color: var(--color-black);
    margin-bottom: 12px;
    text-align: center;
  }

  .block{
    display: flex;
    align-items: center;
    justify-content: space-between;
    gap: 12px;

    &-btn{
      display: flex;
      flex-direction: column;
      align-items: center;
      gap: 4px;

      &-title{
        font-size: 12px;
        line-height: 20px;
        font-weight: 500;
        color: var(--color-gray-80);
      }

      &-active{
        .btn{
          background: var(--color-purple) !important;
        }
        .block-btn-title{
          color: var(--color-purple);
        }
      }
    }

    .btn{
      display: flex;
      align-items: center;
      justify-content: center;
      position: relative;
      border-radius: 12px;
      border: 0;
      height: 74.75px;
      width: 74px;
      background: var(--color-white);

      .svg{
        position: absolute;
        top: 50%;
        left: 50%;
        transform: translate(-50%,-50%);
      }

      img{
        object-fit: cover;
        display: block;
        max-width: 48px;
        max-height: 48px;
      }

      .hamburger{
        width: 59px;
        height: 58px;
      }
    }
  }
}
</style>

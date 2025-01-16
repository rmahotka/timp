<script setup>
import {computed, onMounted, ref} from "vue";

const personnelList = ref([
  {id: 1, name: 'Madison', position: 'Waiter', img:'personnel-1.png'},
  {id: 2, name: 'Den', position: 'Cook', img:'personnel-2.png'},
  {id: 3, name: 'Igor', position: 'Waiter', img:'personnel-3.png'},
  {id: 4, name: 'Pavel', position: 'Chef', img:'personnel-2.png'}
]);

const currentIndex = ref(0);

const nextSlide = () => {
  currentIndex.value = (currentIndex.value + 1) % personnelList.value.length;
};

onMounted(() => {
  setInterval(nextSlide, 3000);
});

const visibleSlides = computed(() => {
  const length = personnelList.value.length;
  return [
    personnelList.value[(currentIndex.value - 1 + length) % length], // Left
    personnelList.value[currentIndex.value],                       // Center
    personnelList.value[(currentIndex.value + 1) % length]         // Right
  ];
});
</script>


<template>
<section class="personnel">
  <div class="personnel-block">
    <div
        v-for="(personnel, index) in visibleSlides"
        :key="personnel.id"
        class="personnel-slide"
        :class="{
          'personnel-center': index === 1,
          'personnel-extremes personnel-extremes-left': index === 0,
          'personnel-extremes personnel-extremes-right': index === 2,
        }"
    >
      <img :src="personnel.img" :alt="personnel.name" class="personnel-img" />
      <div v-if="index === 1" class="personnel-info">
        <h3 class="personnel-info-name">{{ personnel.name }}</h3>
        <p class="personnel-info-position">{{ personnel.position }}</p>
      </div>
    </div>
  </div>
</section>
</template>

<style scoped lang="scss">
.personnel{
  position: relative;
  max-width: 1000px;
  margin: 16px auto 20px;
  display: flex;
  align-items: center;
  overflow: hidden;

  &-block {
    position: relative;
    display: flex;
    align-items: center;
    justify-content: center;
    width: 100%;
  }

  &-slide {
    display: flex;
    align-items: center;
    transition: transform 0.6s ease, opacity 0.6s ease;
  }

  &-extremes{
    position: absolute;
    height: 66px;
    object-fit: cover;
    border-radius: 100px;
    opacity: 0.2;
    overflow: hidden;

    &-left{
      left: 0;
      transform: translateX(-50%);
    }

    &-right{
      right: 0;
      transform: translateX(50%);
    }
  }

  &-center{
    display: flex;
    align-items: center;
    justify-content: center;
    gap: 12px;
  }

  &-info{
    &-name{
      color: var(--color-black-0f);
      font-size: 22px;
      line-height: 24px;
      font-weight: 600;
      margin-bottom: 4px;
    }
    &-position{
      color: var(--color-purple);
      font-size: 16px;
      line-height: 20px;
      font-weight: 600;
    }
  }

  &-img{
    width: 92px;
    height: 92px;
    object-fit: cover;
    border-radius: 100px;
  }
}
</style>

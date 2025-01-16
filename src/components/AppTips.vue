<script setup>


const model = defineModel()
</script>

<template>
<div class="tips">
  <div class="tips-text">
    <p class="title">I want Mark to receive <br/> the full amount</p>
    <p class="description">You compensate service fee of 0.00€, which will be applied to your payment.</p>
  </div>
  <div class="toggle-switch">
    <input type="checkbox" id="switch" v-model="model" />
    <label for="switch" class="slider"></label>
  </div>

</div>
</template>

<style scoped lang="scss">
.tips{
  display: flex;
  align-items: center;
  justify-content: space-between;
  gap: 8px;
  background: var(--color-white);
  padding: 16px;
  border-radius: 12px;

  &-text{
    flex: 0 1 auto;

    .title{
      font-size: 14px;
      line-height: 20px;
      font-weight: 500;
      color: var(--color-black);
      margin-bottom: 4px;
    }

    .description{
      font-size: 14px;
      line-height: 20px;
      font-weight: 400;
      color: var(--color-gray-80);
    }
  }

  .toggle-switch {
    position: relative;
    min-width: 54px;
    width: 54px;
    height: 30px;
  }

  .toggle-switch input {
    opacity: 0;
    width: 0;
    height: 0;
  }

  .slider {
    position: absolute;
    cursor: pointer;
    top: 0;
    left: 0;
    right: 0;
    bottom: 0;
    background-color: var(--color-purple-radio);
    border-radius: 22px;
    transition: 0.4s;
  }

  .slider:before {
    position: absolute;
    content: "";
    height: 24px;
    width: 24px;
    left: 3px;
    bottom: 3px;
    background-color: var(--color-white);
    border-radius: 50%;
    box-shadow: 0 4px 4px 0 #00000033;
    transition: 0.4s;
  }

  input:checked + .slider {
    background-color: var(--color-purple);
  }

  input:checked + .slider:before {
    transform: translateX(25px);
  }

}
</style>

<script setup>
const model = defineModel()

const setAmount = (val) => {
  model.value = val
}

const amounts = [2, 5, 100];

</script>

<template>
  <div class="form-block">
    <div class="form-block-amount">
      <p class="form-block-title">Enter amount of tips</p>
      <p class="amount"
         :class="{'amount-null':!model}"
      >
        {{model}}€
      </p>
    </div>
    <div class="form-block-btn">
      <button
          v-for="value in amounts"
          :key="value"
          class="btn"
          :class="{ 'btn-active': model === value }"
          @click="setAmount(value)"
      >
        {{ value }}
      </button>
    </div>
  </div>
</template>

<style scoped lang="scss">
.form{
  margin-bottom: 8px;

  &-block{
    margin-bottom: 12px;

    &-amount{
      background: var(--color-white);
      border-radius: 20px;
      padding: 12px 0 16px 0;
      margin-bottom: 8px;
    }

    &-title{
      color: var(--color-black);
      text-align: center;
      margin-bottom: 8px;
    }

    .amount{
      text-align: center;
      font-size: 34px;
      line-height: 36px;
      font-weight: 700;
      color: var(--color-black-0f);

      &-null{
        color: var(--color-black);
        opacity: 0.1;
      }
    }

    &-btn{
      display: flex;
      align-items: center;
      justify-content: space-between;
      gap: 4px;

      .btn{
        border: 0;
        font-size: 13px;
        line-height: 18px;
        font-weight: 600;
        background: var(--color-white);
        color: var(--color-black-1f);
        width: 100%;
        text-align: center;
        border-radius: 12px;
        padding: 8px 0;

        &-active{
          background: var(--color-purple);
          color: var(--color-white);;
        }
      }
    }
  }
}
</style>

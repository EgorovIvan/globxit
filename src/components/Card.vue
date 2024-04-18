<script setup>

defineProps({
  id: Number,
  name: String,
  email: String,
  phone: String,
  onClickCard: Function,
})

</script>

<template>
  <div>

    <div class="card" @click="onClickCard">

      <div class="card__title">
        {{ name }}
      </div>

      <div class="card__item">
        <div class="card__img-tel"></div>
        {{ phone }}
      </div>

      <div class="card__item">
        <div class="card__img-mail"></div>
        {{ email }}
      </div>

    </div>
  </div>
</template>

<style scoped lang="less">
.card {
  width: 357px;
  height: 314px;
  padding: 24px;
  border-radius: 16px;
  box-sizing: border-box;
  box-shadow: 0 0 20px 0 rgba(0, 0, 0, 0.1);
  cursor: pointer;

  &__title {
    font-family: 'Proxima-Nova', sans-serif;
    font-weight: 700;
    font-size: 24px;
    line-height: 30px;
    color: #262C40;
    margin-bottom: 24px;
  }

  &__item {
    display: flex;
    align-items: center;
    font-family: 'Proxima-Nova', sans-serif;
    font-weight: 400;
    font-size: 14px;
    line-height: 20px;
    color: #8189A3;
    margin-bottom: 14px;
  }

  &__img-tel {
    width: 14px;
    height: 24px;
    margin: 0 19px 0 5px;
    background: url(../../public/tel.svg) no-repeat;
    background-size: contain;
  }

  &__img-mail {
    width: 24px;
    height: 14px;
    margin: 0 14px 0 0;
    background: url(../../public/mail.svg) no-repeat;
    background-size: contain;
  }
}
</style>
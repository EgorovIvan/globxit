<script setup>

defineProps({
  modalItem: Object,
})

const emit = defineEmits(['closeModal'])

</script>

<template>
  <div class="modal" @click="emit('closeModal')">

    <div class="modal__content" @click.stop>

      <div class="modal__title">
        {{ modalItem.name }}
      </div>

      <div @click="emit('closeModal')" class="modal__close"></div>

      <div class="modal__info">
        <div class="modal__info-title">
          Телефон:
        </div>
        <div class="modal__info-item">
          {{ modalItem.phone }}
        </div>
        <div class="modal__info-title">
          Почта:
        </div>
        <div class="modal__info-item">
          {{ modalItem.email }}
        </div>
        <div class="modal__info-title">
          Дата приема:
        </div>
        <div class="modal__info-item">
          {{ modalItem.hire_date }}
        </div>
        <div class="modal__info-title">
          Должность:
        </div>
        <div class="modal__info-item">
          {{ modalItem.position_name }}
        </div>
        <div class="modal__info-title">
          Подразделение:
        </div>
        <div class="modal__info-item">
          {{ modalItem.department }}
        </div>
      </div>

      <div class="modal__desc">
        <div class="modal__info-title">
          Дополнительная информация:
        </div>
        <div class="modal__info-item">
          Разработчики используют текст в качестве заполнителя макeта страницы.
          Разработчики используют текст в качестве заполнителя макeта страницы.
        </div>
      </div>
    </div>

  </div>
</template>

<style scoped lang="less">
.modal {
  position: fixed;
  top: 0;
  left: 0;
  right: 0;
  bottom: 0;
  background-color: rgba(188, 195, 208, 0.5);
  z-index: 5;

  &__content {
    position: absolute;
    left: 50%;
    top: 50%;
    transform: translate(-50%, -50%);
    width: 500px;
    min-height: 468px;
    padding: 24px;
    border-radius: 16px;
    box-sizing: border-box;
    box-shadow: 0 0 20px 0 rgba(0, 0, 0, 0.1);
    background-color: #FFFFFF;
    z-index: 10;
  }

  &__close {
    position: absolute;
    top: 28px;
    right: 24px;
    width: 20px;
    height: 20px;
    background: url(../../public/close.svg) no-repeat;
    background-size: contain;
    cursor: pointer;
  }

  &__title {
    font-family: 'Proxima-Nova', sans-serif;
    font-weight: 700;
    font-size: 24px;
    line-height: 30px;
    color: #262C40;
    margin-bottom: 40px;
  }

  &__info {
    display: grid;
    grid-template-columns: min-content auto;
    gap: 14px 30px;
    margin-bottom: 40px;
  }

  &__info-title {
    font-family: 'Proxima-Nova', sans-serif;
    font-weight: 400;
    font-size: 18px;
    line-height: 24px;
    color: #262C40;
  }

  &__info-item {
    display: flex;
    align-items: center;
    font-family: 'Proxima-Nova', sans-serif;
    font-weight: 400;
    font-size: 16px;
    line-height: 24px;
    color: #8189A3;
  }

  &__desc {
    display: flex;
    flex-direction: column;
    align-items: start;
    justify-content: start;
    gap: 12px;
  }
}
</style>
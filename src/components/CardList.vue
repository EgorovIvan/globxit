<script setup>

import Card from "@/components/Card.vue";

defineProps({
  items: Array,
})

const emit = defineEmits(['showItem'])

</script>

<template>
  <div class="main__users-list" v-auto-animate>
    <Card
    v-for="item in items"
    :key="item.phone"
    :id="item.phone"
    :name="item.name"
    :phone="item.phone"
    :email="item.email"
    :onClickCard="() => emit('showItem', item)"
    />
  </div>
</template>

<style scoped lang="less">

</style>
<script setup>
import Card from "@/components/Card.vue";
import {onMounted, reactive, ref, watch} from "vue";
import axios from "axios";
import debounce from "lodash.debounce";
import CardList from "@/components/CardList.vue";
import Modal from "@/components/Modal.vue";

const items = ref([]);
const modalItem = ref({});

const showModal = ref(false);
const searchQuery = reactive({
  term: ''
});

const onChangeSearchInput = debounce((event) => {
  searchQuery.term = event.target.value
}, 500);

const onClickCard = (item) => {
  modalItem.value = item
  showModal.value = true
}

const closeModal = () => {
  showModal.value = false
  modalItem.value = {}
}

const fetchItems = async () => {
  try {
    const params = {
      term: searchQuery.term,
    }

    if (searchQuery.term) {
      params.term = `${searchQuery.term}`
    }
    const {data} = await axios.get('http://127.0.0.1:3000', {
      params
    });

    items.value = data;
  } catch (err) {
    console.log(err);
  }
}

onMounted(async () => {
  await fetchItems();
});

watch(searchQuery, fetchItems);

</script>

<template>
  <div class="main">
    <div class="search">

      <input @input="onChangeSearchInput" type="text" class="search__input">

      <div class="search__img"></div>

    </div>

    <Modal
        v-show="showModal"
        :modalItem="modalItem"
        @close-modal="closeModal"
    />

    <CardList
        :items="items"
        @show-item="onClickCard"
    />
  </div>
</template>

<style scoped lang="less" >
.main {
  width: 1280px;
  min-height: 100vh;
  margin: 0 auto;
  padding: 64px 80px;
  box-sizing: border-box;

  &__users-list {
    display: grid;
    grid-template-columns: repeat(3, min-content);
    gap: 24px;
  }
}

.search {
  position: relative;

  &__input {
    width: 100%;
    height: 48px;
    margin-bottom: 32px;
    padding: 0 20px;
    font-family: 'Proxima-Nova', sans-serif;
    font-weight: 400;
    font-size: 18px;
    line-height: 24px;
    color: #262C40;
    border: 1px solid #D4DEFE;
    border-radius: 24px;
  }

  &__img {
    position: absolute;
    top: 12px;
    right: 24px;
    width: 19.61px;
    height: 19.61px;
    margin: 2px;
    background: url(../public/search.svg) no-repeat;
    background-size: contain;
    cursor: pointer;
  }
}
</style>

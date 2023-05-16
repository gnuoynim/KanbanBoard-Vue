<template>
  <div>
    <h1>ts-vue 로 만드는 KanbanBoard</h1>
    텍스트 입력<input v-model="inputValue" @keyup.enter="addItem" />
    <ul>
      <li v-for="(item, index) in items" :key="index">
        {{ item.value }}
        {{ item.id }}
        <button type="button" @click="clickValue = index; inputValue = item.value; modal = true;">자세한 일정 추가하기</button>
      </li>
    </ul>
    <Modal v-if="modal" :modal="modal" :item="inputValue" :clickValue="clickValue" @closeModal="modal = false" @select="selectOption"/>
  </div>
</template>


<script setup lang="ts">
import { ref } from 'vue'
import Modal from './components/modal.vue'

const inputValue = ref<string>('');
const items = ref<Array<{ id: number; value: string }>>([]);
const modal = ref<Boolean>(false);
const clickValue = ref<Number>(0); // 클릭한값
const selection = ref<String>('')

const addItem = () => {
  items.value.push({id:Date.now(), value:inputValue.value})
  inputValue.value = '' 
}


</script>


<style scoped></style>

<script setup lang="ts">
import { ref} from 'vue'
import Modal from './components/modal.vue'

const inputValue = ref<string>('');
const items = ref<string[]>([]);

const addItem = () => {
  items.value.push(inputValue.value)
  inputValue.value = '' // 입력 필드를 초기화
}
</script>

<template>
  <div>
    <h1>ts-vue 로 만드는 KanbanBoard</h1>

    텍스트 입력<input v-model="inputValue" @keyup.enter="addItem" />
    <ul>
      <li v-for="(item, index) in items" :key="index">{{ item }}</li>
    </ul>
    <Modal/>
  </div>
</template>



<style scoped></style>

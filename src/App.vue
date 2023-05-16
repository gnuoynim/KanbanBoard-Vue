<template>
  <div>
    <h1>ts-vue 로 만드는 KanbanBoard</h1>
    {{ selectedValue }}
    텍스트 입력<input v-model="inputValue" @keyup.enter="addItem" />
    <ul>
      <li v-for="(item, index) in items" :key="index">

        {{ item }}
        <button type="button" @click="clickValue = index; selectedValue = item; modal = true;">자세한 일정 추가하기</button>
      </li>
    </ul>
    <Modal v-if="modal" :modal="modal" :item="selectedValue" :clickValue="clickValue" @closeModal="modal = false"/>
  </div>
</template>


<script setup lang="ts">
import { ref } from 'vue'
import Modal from './components/modal.vue'

const inputValue = ref<string>('');
const items = ref<string[]>([]);
const modal = ref<Boolean>(false);
const clickValue = ref<Number>(0); // 클릭한값
const selectedValue = ref<string>('')



const addItem = () => {
  items.value.push(inputValue.value)
  inputValue.value = '' // 입력 필드를 초기화
}
const handleSelect = (selectedOption: string) => {

}
</script>


<style scoped></style>

<template>
  <div class="modal" v-if="modal">
    <div class="modalContainer">
      <h1>modal</h1>
      <div class="addList">
        {{ clickValue }}
        {{ item }}
        <button type="button" @click.stop="$emit('closeModal')" class="closeButton">X</button>
      </div>
      <div class="checkBox">
        <input v-model="checkInput" @keyup.enter="addCheckbox" />
        <div>
          {{ selectOption }}
          <select v-model="selectOption">
            <option>Todo</option>
            <option>Doing</option>
            <option>Done</option>
          </select>
        </div>
        <ul>
          <li v-for="(item, index) in checkList" :key="index">{{ item }}</li>
        </ul>
        <button type="button" @click.stop="$emit('select', selectOption)">button</button>
      </div>
    </div>
  </div>
</template>


<script setup lang="ts">
import { ref } from 'vue'

const checkList = ref<String[]>([])
const checkInput = ref<String>('')
const selectOption = ref<String>('')

const addCheckbox = () => {
  checkList.value.push(checkInput.value)
  checkInput.value = '' // 입력 필드를 초기화
}

const props = defineProps<{
  modal: Boolean,
  item: string,
  clickValue: Number,
}>()

</script>

<style scoped>
.modal {
  position: fixed;
  top: 0;
  left: 0;
  width: 100%;
  height: 100%;
  background-color: rgba(0, 0, 0, 0.685);
}

.modalContainer {
  position: absolute;
  left: 50%;
  top: 50%;
  transform: translate3d(-50%, -50%, 0);
  width: 500px;
  height: 440px;
  background-color: #fff;
  border-radius: 20px;

}
</style>
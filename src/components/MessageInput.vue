<script setup>

import {ref} from "vue";
const emit = defineEmits(['sendMessage'])

const newMessage = ref('')
function addMessage() {
  if (newMessage.value.trim() === '') return
  emit('sendMessage', newMessage.value.trim())
  newMessage.value = ''
}
</script>

<template>
  <form class="message-input" @submit.prevent="addMessage">
    <input v-model="newMessage" type="text" placeholder="Введите сообщение…" />
    <button type="submit">ОТПРАВИТЬ</button>
  </form>
</template>

<style scoped>
.message-input {
  width: 601px;
  display: flex;
  gap: 16px;
}

.message-input input {
  flex: 1;
  height: 40px;
  padding: 0 12px;
  border-radius: 8px;
  border: 1px solid #DEE2E8;
  font-size: 14px;
}

.message-input button {
  width: 120px;
  background: linear-gradient(180deg, #04694B 0%, #11A87B 100%);
  border: none;
  border-radius: 8px;
  color: white;
  font-weight: 700;
  font-size: 14px;
  cursor: pointer;
  transition: background-color 0.3s;
}

.message-input button:hover {
  background: linear-gradient(180deg, #035b3b 0%, #0f8a58 100%);
}

@media (max-width: 768px) {
  .message-input {
    width: 100%;
    gap: 8px;
  }
}

@media (max-width: 480px) {
  .message-input {
    display: flex;
    flex-direction: column;
    align-items: center;
    width: 100%;
    gap: 15px;
  }

  .message-input input {
    width: 90%;
    padding: 0 12px;
    box-sizing: border-box;
    font-size: 14px;
    line-height: 40px;
  }

  .message-input button {
    width: 90%;
    height: 40px;
    font-size: 14px;
  }

}
</style>
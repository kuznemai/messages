<script setup>
import Message from "@/components/Message.vue";
import MessageList from "@/components/MessageList.vue";
import MessageInput from "@/components/MessageInput.vue";
import {ref} from "vue";

const messages = ref([
  { id: 1, text: 'Привет!', createdAt: new Date(), removed: false },
  { id: 2, text: 'Как дела?', createdAt: new Date(), removed: false },
  { id: 3, text: 'Vue.js классный!', createdAt: new Date(), removed: false }
])
let lastId = messages.value.length

function addMessage(message) {
  lastId++
  messages.value.push({ id: lastId, text: message, createdAt: new Date(), removed: false })
  console.log(message)
}
function removeMessage(id){
  const message = messages.value.find(msg => msg.id === id)
  if(message){
    message.removed = true
  }
}
</script>

<template>
  <main class="chat">
    <Message :messages="messages" @sendId="removeMessage"></Message>
    <MessageList :messages="messages"></MessageList>
    <MessageInput @send-message="addMessage"></MessageInput>
  </main>
</template>

<style scoped>
.chat {
  display: flex;
  flex-direction: column;
  align-items: center;
  justify-content: center;
  width: 665px;
  height: 541px;
  border-radius: 8px;
  border: 1px solid #e0e0e0;
  gap: 24px;
}

</style>

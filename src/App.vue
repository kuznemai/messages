<script setup>
import Message from "@/components/Message.vue";
import MessageList from "@/components/MessageList.vue";
import MessageInput from "@/components/MessageInput.vue";
import {onMounted, ref} from "vue";

const messages = ref([
  { id: 1, text: 'Привет!', createdAt: new Date(), removed: false },
  { id: 2, text: 'Как дела?', createdAt: new Date(), removed: false },
  { id: 3, text: 'Сообщение 3', createdAt: new Date(), removed: false }
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
const currentMessage = ref(null)
let index = 0
function startShowingMessages() {
  setInterval(() => {
    const visibleMessages = messages.value.filter(m => !m.removed);
    if (visibleMessages.length === 0) {
      currentMessage.value = null
      return
    }
    currentMessage.value = visibleMessages[index % visibleMessages.length]
    index++
  }, 2000);
}
onMounted(startShowingMessages);
</script>

<template>
  <main class="chat">
    <Message  v-if="currentMessage" :message="currentMessage" @sendId="removeMessage"></Message>
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
  padding: 16px 8px;
}
@media (max-width: 768px) {
  .chat {
    width: 100%;
    justify-content: space-between;
  }
  .message-item .date {
    font-size: 11px;
  }
}

@media (max-width: 480px) {
  .chat {
    width: 100%;
    flex-direction: column;
    justify-content: space-around;
  }
  .message-item .date {
    font-size: 10px;
  }
}

</style>

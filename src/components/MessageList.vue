<script setup>
const props = defineProps({
  messages: Array
})
function formatDate(date) {
  return new Date(date).toLocaleString('ru-RU', {
    day: '2-digit', month: '2-digit', year: 'numeric',
    hour: '2-digit', minute: '2-digit', second: '2-digit'
  })
}
</script>

<template>
  <section class="message-list">
    <ul>
      <li v-for="msg in messages" :key="msg.id" class="message-item">
        <span v-if="msg.removed" class="icon">×</span>
        <span class="text">{{ msg.text }}</span>
        <span class="date">{{ formatDate(msg.createdAt) }}</span>
      </li>
    </ul>
  </section>
</template>

<style scoped>
.message-list {
  width: 601px;
  height: 307px;
  overflow-y: auto;
  padding: 16px;
  background-color: #F6F8FA;
  border-radius: 6px;
  font-size: 14px;
  box-sizing: border-box;
}

.message-list ul {
  list-style: none;
  padding: 0;
  margin: 0;
}

.message-item {
  display: flex;
  align-items: center;
  gap: 8px;
  padding: 8px 0;
  border-bottom: 1px solid #e0e0e0;
  word-break: break-word;
}

.message-item .icon {
  color: red;
  font-size: 18px;
  font-weight: bold;
  margin-right: 4px;
}

.message-item .text {
  flex: 1;
  color: #000000;
}

.message-item .date {
  color: #666;
  font-size: 12px;
  white-space: nowrap;
}


@media (max-width: 768px) {
  .message-list {
    width: 100%;
    padding: 12px;
    font-size: 13px;
  }
  .message-item .date {
    font-size: 11px;
  }
}

@media (max-width: 480px) {
  .message-list {
    padding: 10px;
  }
  .message-item {
    flex-direction: column;
    align-items: flex-start;
    gap: 4px;
  }
  .message-item .date {
    font-size: 10px;
  }
}

</style>
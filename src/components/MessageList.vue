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
      <li v-for="msg in messages" :key="msg.id" :class="{ removed: msg.removed }">
<!--        <span class="status">{{ msg.removed ? '×' : '' }}</span>-->
        <span class="text">{{ msg.text }}</span>
        <span class="date">{{ formatDate(msg.createdAt) }}</span>
      </li>
    </ul>
  </section>
</template>

<style scoped>
.message-list {
  width: 601px;
  max-height: 307px;
  overflow-y: auto;
  padding: 16px;
  background-color: #F6F8FA;
  border-radius: 6px;
  font-size: 14px;
}

.message-list ul {
  list-style: none;
  padding: 0;
  margin: 0;
}

.message-list li {
  display: flex;
  align-items: center;
  gap: 8px;
  padding: 4px 0;
  border-bottom: 1px solid #e0e0e0;
}

.message-list li.removed {
  color: #aaa;
  text-decoration: line-through;
}

.status {
  width: 16px;
  color: red;
  font-weight: bold;
}

.text {
  flex: 1;
}

.date {
  color: #666;
  white-space: nowrap;
}
</style>
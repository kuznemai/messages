<script setup>
const props = defineProps({
  message: Object
})
const emit = defineEmits(['sendId'])
function removeMessage(id){
  emit('sendId', id)
}
</script>

<template>
  <div class="message">
    <div class="left">
      <button class="remove_btn" @click="removeMessage(message.id)">×</button>
    </div>
    <div class="right">
      <p>{{ message.text }}</p>
    </div>
  </div>
</template>

<style scoped>
.message {
  display: flex;
  align-items: flex-start;
  gap: 12px;
  width: 100%;
  max-width: 601px;
  padding: 10px;
  background-color: #E4F0ED;
  border-radius: 8px;
  box-sizing: border-box;
}

.left {
  flex-shrink: 0;
}

.right {
  display: flex;
  flex-direction: column;
  flex: 1;
}

.remove_btn {
  width: 24px;
  height: 24px;
  font-size: 18px;
  font-weight: bold;
  line-height: 1;
  text-align: center;
  background: none;
  border: none;
  color: #333;
  cursor: pointer;
}

/* Адаптив под мобильные */
@media (max-width: 480px) {
  .message {
    gap: 10px;
    padding: 8px;
  }

  .remove_btn {
    width: 22px;
    height: 22px;
    font-size: 16px;
  }

  .right p {
    margin: 0;
    font-size: 14px;
  }
}
</style>
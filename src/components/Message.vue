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
    <button class="remove_btn" @click="removeMessage(message.id)">×</button>
    <p> {{ message.text }}</p>
  </div>
</template>

<style scoped>
.message {
  display: flex;
  flex-direction: row;
  align-items: center;
  gap: 10px;
  width: 601px;
  height: 72px;
  background-color: #E4F0ED;
  border: none;
}
.remove_btn{
  width: 20px;
  height: 20px;
  margin-left: 6px;
}
@media (max-width: 768px) {
  .message {
    width: 100%;
    height: 60px;
    font-size: 14px;
  }
  .remove_btn {
    width: 22px;
    height: 22px;
    font-size: 12px;
  }
}


@media (max-width: 480px) {
  .message {
    width: 100%;
    height: auto;
    padding: 8px 12px;
    font-size: 14px;
  }
  .remove_btn {
    width: 20px;
    height: 20px;
    font-size: 12px;
  }
  p {
    flex: 1 1 100%;
    margin: 0;
  }
}
</style>

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
}
</style>

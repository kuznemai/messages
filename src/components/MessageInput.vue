<script setup>
import { computed, ref } from "vue";
const emit = defineEmits(["sendMessage"]);

const newMessage = ref("");
const isDisabled = computed(() => {
  if (newMessage.value.trim().length < 1) {
    return true;
  }
  return false;
});

function addMessage() {
  emit("sendMessage", newMessage.value.trim());
  newMessage.value = "";
}
</script>

<template>
  <form class="message-input" @submit.prevent="addMessage">
    <input v-model="newMessage" type="text" placeholder="Введите сообщение…" />
    <button
      type="submit"
      :class="{ disabled: isDisabled }"
      :disabled="isDisabled"
    >
      ОТПРАВИТЬ
    </button>
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
  border: 1px solid #dee2e8;
  font-size: 14px;
}

.message-input button {
  width: 120px;
  background: linear-gradient(180deg, #04694b 0%, #11a87b 100%);
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
.message-input button.disabled {
  cursor: default;
  background: linear-gradient(180deg, #676767 0%, #858686 100%);
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
    width: 100%;
    height: 40px;
    padding: 0 12px;
    box-sizing: border-box;
    font-size: 16px;
    line-height: 40px;
    appearance: none;
    -webkit-appearance: none;
    -moz-appearance: none;
  }
  .message-input button {
    width: 100%;
    height: 40px;
    font-size: 14px;
  }
}
</style>

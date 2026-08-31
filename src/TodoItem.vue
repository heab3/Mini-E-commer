<script setup>
defineProps({
  title: String,
  completed: Boolean
})

const emit = defineEmits(['toggle', 'delete'])
</script>

<template>
  <div class="task" :class="{ 'is-completed': completed }">

    
    <button
      class="checkbox"
      :class="{ checked: completed }"
      @click="emit('toggle')"
    >
      <span v-if="completed" class="checkmark">✓</span>
    </button>

    
    <span class="task-text">
      {{ title }}
    </span>

    
    <button class="delete-btn" @click="emit('delete')">
      <svg xmlns="http://w3.org" width="14" height="14" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"><path d="M3 6h18"></path><path d="M19 6v14c0 1-1 2-2 2H7c-1 0-2-1-2-2V6"></path><path d="M8 6V4c0-1 1-2 2-2h4c1 0 2 1 2 2v2"></path></svg>
    </button>

  </div>
</template>

<style scoped>
.task {
  height: 45px;
  display: flex;
  align-items: center;
  border-bottom: 1px solid white;
  padding: 0 5px;
}

.task:last-child {
  border-bottom: none; 
}


.checkbox {
  width: 22px;
  height: 22px;
  border: 2px solid #7c7267;
  border-radius: 50%;
  background: transparent;
  margin-right: 12px;
  cursor: pointer;
  display: flex;
  align-items: center;
  justify-content: center;
  padding: 0;
  transition: all 0.2s;
}


.task.is-completed .checkbox {
  border-color: #df8c25;
  background-color: transparent;
}

.checkmark {
  color: #df8c25;
  font-size: 14px;
  font-weight: bold;
}

.task-text {
  flex: 1;
  font-size: 15px;
  color: #4a3f35;
  font-weight: 500;
}


.task.is-completed .task-text {
  color: #c4b9ad;
  text-decoration: line-through;
}


.delete-btn {
  border: none;
  background: transparent;
  cursor: pointer;
  color: #df9898;
  display: flex;
  align-items: center;
  padding: 5px;
  transition: color 0.2s;
}

.delete-btn:hover {
  color: #dc3545;
}
</style>

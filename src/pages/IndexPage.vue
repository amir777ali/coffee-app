<template>
  <q-page class="q-pa-md">
    <div class="row q-mb-md">
      <q-input
        filled
        v-model="newTask"
        label="Add a new task"
        @keyup.enter="addTask"
      />
      <q-btn label="Add Task" color="primary" @click="addTask" />
    </div>

    <div>
      <q-list bordered padding>
        <q-item v-for="(task, index) in tasks" :key="index">
          <q-item-section>
            <q-checkbox v-model="task.done" />
          </q-item-section>
          <q-item-section>
            <span :class="{ 'line-through': task.done }">{{ task.text }}</span>
          </q-item-section>
          <q-item-section side>
            <q-btn
              flat
              icon="delete"
              color="negative"
              @click="removeTask(index)"
            />
          </q-item-section>
        </q-item>
      </q-list>
    </div>
  </q-page>
</template>

<script setup>
import { ref } from "vue";

const newTask = ref("");
const tasks = ref([]);

const addTask = () => {
  if (newTask.value.trim()) {
    tasks.value.push({ text: newTask.value, done: false });
    newTask.value = "";
  }
};

const removeTask = () => {
  tasks.value.splice(index, 1);
};

// http://localhost:9000/#/
</script>

<style>
.q-mb-md {
  color: green;
}
.line-through {
  text-decoration: line-through;
}
</style>

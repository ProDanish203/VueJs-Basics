<script setup lang="ts">
import { ref } from "vue";

defineProps<{
  title: String;
}>();

const userStatus: string = "asdsad";
const todos = ref<Array<{ id: number; text: string }>>([
  { id: 1, text: "Learn Vue" },
  { id: 2, text: "Build something awesome" },
  { id: 3, text: "Profit!" },
]);

const addTodo = (text: string) => {
  const newTodo = {
    id: todos.value.length + 1,
    text: text,
  };
  todos.value.push(newTodo);
};

const removeTodo = (id: number) => {
  todos.value = todos.value.filter((todo) => todo.id !== id);
};

const bindLink = "https://vuejs.org/";
const count = ref(0);
</script>

<template>
  <div class="flex flex-col items-center">
    <!-- Template rendering -->
    <h1 class="text-3xl font-semibold text-center mb-10">{{ title }}</h1>

    <!-- Conditionals -->
    <p v-if="userStatus === 'active'">User is active</p>
    <p v-else-if="userStatus === 'inactive'">User is inactive</p>
    <p v-else>User status is unknown</p>

    <!-- Looping -->
    <div class="mt-4 w-full max-w-2xl">
      <input
        type="text"
        placeholder="New todo"
        class="p-2 border border-neutral-800 rounded-md w-full"
        @keyup.enter="
          console.log(($event.target as unknown as any)?.value as string);
          addTodo(($event.target as unknown as any)?.value as string);
          ($event.target as unknown as any).value = '';
        "
      />
      <div class="grid grid-cols-3 my-4">
        <div
          v-for="value in todos"
          :key="value.id"
          class="relative p-4 border border-neutral-800 overflow-hidden"
        >
          <p>
            {{ value.text }}
          </p>
          <div class="flex items-center gap-x-2 mt-2">
            <button
              @click="removeTodo(value.id)"
              class="bg-red-500 text-white w-full rounded-md cursor-pointer"
            >
              X
            </button>
            <button
              class="bg-green-500 text-neutral-900 w-full rounded-md cursor-pointer"
            >
              Edit
            </button>
          </div>
        </div>
      </div>
    </div>

    <!-- Attribute Binding -->
    <!-- <a v-bind:href="bindLink" target="_blank" class="text-blue-500 underline"
      >Vue.js Official Website</a
    > -->
    <a :href="bindLink" target="_blank" class="text-blue-500 underline"
      >Vue.js Official Website</a
    >

    <!-- Event Handling -->
    <div class="my-2">
      <p class="text-2xl font-semibold text-center">{{ count }}</p>
      <div class="flex items-center gap-x-2 mt-2">
        <button
          @click="count++"
          class="py-2 px-4 bg-neutral-800 hover:bg-neutral-900 cursor-pointer rounded-md"
        >
          Count Up
        </button>
        <button
          @click="count > 0 ? count-- : null"
          class="py-2 px-4 bg-neutral-800 hover:bg-neutral-900 cursor-pointer rounded-md"
        >
          Count Down
        </button>
      </div>
    </div>
  </div>
</template>

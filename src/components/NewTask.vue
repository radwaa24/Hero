<template>
  <div v-if="show" class="fixed inset-0 z-10 overflow-y-auto">
    <div
      class="flex items-center justify-center min-h-screen pt-4 px-4 pb-20 text-center"
    >
      <div class="fixed inset-0 transition-opacity" aria-hidden="true">
        <div class="absolute inset-0 bg-gray-100 opacity-75"></div>
      </div>
      <div
        class="inline-block rounded-lg shadow-xl transform transition-all mx-auto max-w-lg w-full"
      >
        <div class="bg-white rounded-lg shadow-xl p-5">
          <div class="">
            <div>
              <h3 class="text-lg font-bold leading-6 text-gray-950">
                Add New Task
              </h3>
              <div class="mt-2">
                <label class="block text-left font-semibold mb-2">
                  Select a color:
                </label>
                <div class="flex space-x-2">
                  <span
                    v-for="color in colors"
                    :key="color"
                    :class="[color, 'h-8 w-8 rounded-full cursor-pointer']"
                    :style="{
                      border:
                        selectedColor === color ? '2px solid black' : 'none',
                    }"
                    @click="selectedColor = color"
                  ></span>
                </div>
              </div>
              <div class="mt-2">
                <label class="block text-left font-semibold mb-2">
                  Select a background color:
                </label>
                <div class="flex space-x-2">
                  <span
                    v-for="color in bgColors"
                    :key="color"
                    :class="[color, 'h-8 w-8 rounded-full cursor-pointer']"
                    :style="{
                      border:
                        selectedBgcolor === color ? '2px solid black' : 'none',
                    }"
                    @click="selectedBgcolor = color"
                  ></span>
                </div>
              </div>
              <div class="mt-4">
                <label class="block text-left font-semibold mb-2">
                  Task name:
                  <input
                    v-model="newTaskName"
                    type="text"
                    class="border-gray-100 shadow-sm rounded-md p-2 mt-1 w-full"
                    placeholder="Enter task Name"
                  />
                </label>
                <label class="block text-left font-semibold mb-2">
                  Task Description:

                  <textarea
                    v-model="newTaskDescription"
                    class="border-gray-100 shadow-sm border rounded-md mt-1 p-2 w-full"
                    placeholder="Enter task Description"
                  ></textarea>
                </label>
                <div class="mt-4">
                  <select
                    v-model="selectedcard"
                    class="border-gray-100 shadow-sm border text-muted focus:border-0 rounded-md p-2 w-full"
                  >
                    <option value="" class="font-bold !text-muted">
                      Where to Add?
                    </option>
                    <option
                      v-for="(card, index) in cards"
                      :key="index"
                      :value="index"
                    >
                      {{ card.title }}
                    </option>
                  </select>
                </div>
              </div>
            </div>
          </div>
          <div class="my-2">
            <button
              @click="addNewTask"
              :disabled="
                !newTaskName || !newTaskDescription || selectedcard === ''
              "
              type="button"
              class="inline-flex justify-center rounded-md border border-transparent shadow-sm px-4 py-2 bg-pink-400 font-semibold text-white hover:bg-pink-300"
            >
              Add Task
            </button>
            <button
              @click="closeModal"
              type="button"
              class="mx-2 inline-flex justify-center rounded-md border shadow-sm px-4 py-2 font-semibold hover:bg-gray-200"
            >
              Cancel
            </button>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script setup>
import { ref } from "vue";

const props = defineProps({
  cards: Array,
  show: Boolean,
});

const emit = defineEmits(["add-task", "close"]);

const newTaskName = ref("");
const newTaskDescription = ref("");
const selectedcard = ref("");
const selectedColor = ref("bg-gray-400");
const selectedBgcolor = ref("bg-yellow-100");

const colors = [
  "bg-purple-400",
  "bg-pink-400",
  "bg-green-400",
  "bg-blue-400",
  "bg-yellow-400",
  "bg-gray-500",
  "bg-pink-800",
  "bg-purple-800",
  "bg-green-800",
  "bg-blue-800",
  "bg-yellow-700",
  "bg-gray-700",
];
const bgColors = [
  "bg-purple-50",
  "bg-pink-50",
  "bg-green-50",
  "bg-blue-50",
  "bg-yellow-50",
  "bg-gray-50",
  "bg-purple-100",
  "bg-pink-100",
  "bg-green-100",
  "bg-blue-100",
  "bg-yellow-100",
  "bg-gray-100",
];
const addNewTask = () => {
  const cardIndex = parseInt(selectedcard.value);
  const newTask = {
    id: generateUniqueId(),
    name: newTaskName.value,
    description: newTaskDescription.value,
    color: selectedColor.value,
    bgColor: selectedBgcolor.value,
  };
  emit("add-task", { task: newTask, cardIndex });
  resetForm();
  emit("close");
};

const closeModal = () => {
  resetForm();
  emit("close");
};

const resetForm = () => {
  newTaskName.value = "";
  newTaskDescription.value = "";
  selectedcard.value = "";
  selectedColor.value = "bg-gray-400";
};

const generateUniqueId = () => {
  return "_" + Math.random().toString(36).substr(2, 9);
};
</script>

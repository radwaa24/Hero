<template>
  <div>
    <div class="grid lg:grid-cols-4 grid-cols-2 gap-4">
      <div
        v-for="(card, index) in cards"
        :key="index"
        class="h-full bg-white rounded-md shadow-md p-3 pb-20"
      >
        <h2 class="text-lg font-semibold mb-4">
          {{ card.title }}
          <span
            class="text-sm font-semibold text-gray-600 ml-3 my-auto border rounded-full p-1"
          >
            {{ card.tasks.length }}
          </span>
          <hr :class="[card.color, 'border-b font-bold my-2']" />
        </h2>
        <div
          class="h-full rounded-lg"
          @drop="addTaskTocard(index)"
          @dragover.prevent
        >
          <div
            v-for="(task, taskIndex) in card.tasks"
            :key="task.id"
            class="p-2 py-3 mb-2 rounded-l-md cursor-pointer relative"
            draggable="true"
            @dragstart="dragstart(task, index)"
            :class="[
              task.bgColor,
              'p-1 mr-2 rounded-l-md text-sm font-medium text-white',
            ]"
          >
            <div class="flex items-start">
              <div>
                <span
                  :class="[
                    task.color,
                    'p-1 px-2 rounded-l-md text-sm font-medium text-white',
                  ]"
                  >Task: {{ task.name }}
                </span>
                <span class="p-1 text-sm text-gray-500">{{
                  task.description
                }}</span>
              </div>
              <!-- Delete task button -->
              <button
                @click="deleteTask(index, taskIndex)"
                class="text-gray-400 pl-2"
              >
                &times;
              </button>
            </div>
          </div>
        </div>
      </div>
    </div>

    <!-- ADDING TASK BUTTON -->
    <div class="mt-4 h-full flex items-end">
      <button
        @click="showAddTaskModal = true"
        class="bg-pink-400 hover:bg-pink-300 font-bold text-white px-4 py-2 rounded-md"
      >
        Add New Task
      </button>
    </div>
    <NewTask
      :cards="cards"
      :show="showAddTaskModal"
      @close="showAddTaskModal = false"
      @add-task="handleAddTask"
    />
  </div>
</template>

<script setup>
import { ref } from "vue";
import NewTask from "./NewTask.vue";

const cards = ref([
  {
    title: "To Do",
    tasks: [
      {
        id: 1,
        name: "Plan",
        description: "Lorem ipsum dolor, sit amet consectetur adipisicingelit.",
        color: "bg-pink-600",
        bgColor: "bg-pink-50",
      },
      {
        id: 2,
        name: "code",
        description: "Lorem ipsum dolor, sit amet consectetur adipisicingelit.",
        color: "bg-purple-400",
        bgColor: "bg-blue-50",
      },
    ],
    color: "border-black",
  },
  {
    title: "In Progress",
    tasks: [
      {
        id: 5,
        name: "Design",
        description: "Lorem ipsum dolor, sit amet consectetur adipisicingelit.",
        color: "bg-yellow-100",
        bgColor: "bg-blue-100",
      },
      {
        id: 6,
        name: "test",
        description: "Lorem ipsum dolor, sit amet consectetur adipisicingelit.",
        color: "bg-blue-500",
        bgColor: "bg-blue-50",
      },
    ],
    color: "border-blue-600",
  },
  {
    title: "QA",
    tasks: [
      {
        id: 3,
        name: "Add",
        initials: "C",
        href: "#",
        members: 16,
        description: "Lorem ipsum dolor, sit amet consectetur adipisicingelit.",
        color: "bg-yellow-500",
        bgColor: "bg-yellow-50",
      },
      {
        id: 7,
        name: "review",
        initials: "F",
        href: "#",
        members: 8,
        description: "Lorem ipsum dolor, sit amet consectetur adipisicingelit.",
        color: "bg-purple-500",
        bgColor: "bg-yellow-100",
      },
    ],
    color: "border-yellow-500",
  },
  {
    title: "Complete",
    tasks: [
      {
        id: 8,
        name: "search",
        description: "Lorem ipsum dolor, sit amet consectetur adipisicingelit.",
        color: "bg-green-400",
        bgColor: "bg-green-50",
      },
      {
        id: 9,
        name: "search",
        description: "Lorem ipsum dolor, sit amet consectetur adipisicingelit.",
        color: "bg-green-600",
        bgColor: "bg-green-100",
      },
      {
        id: 10,
        name: "search",
        description: "Lorem ipsum dolor, sit amet consectetur adipisicingelit.",
        color: "bg-green-800",
        bgColor: "bg-green-50",
      },
    ],
    color: "border-green-500",
  },
]);

const dragItem = ref(null);
const showAddTaskModal = ref(false);

const dragstart = (task, cardIndex) => {
  dragItem.value = { task, cardIndex };
};

const addTaskTocard = (targetcardIndex) => {
  const { task, cardIndex } = dragItem.value;
  if (cardIndex !== targetcardIndex && targetcardIndex !== null) {
    const fromcard = cards.value[cardIndex];
    const tocard = cards.value[targetcardIndex];
    if (fromcard && tocard) {
      fromcard.tasks = fromcard.tasks.filter((t) => t.id !== task.id);
      tocard.tasks.push(task);
    }
  }
};

const handleAddTask = (newTask) => {
  cards.value[newTask.cardIndex].tasks.push(newTask.task);
};

const deleteTask = (cardIndex, taskIndex) => {
  cards.value[cardIndex].tasks.splice(taskIndex, 1);
};
</script>

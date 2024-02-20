<template>
    <div>
        <div class="grid lg:grid-cols-4 grid-cols-2 gap-4">
            <div v-for="(column, index) in columns" :key="index" class="h-full bg-white rounded-md shadow-md p-3 pb-20">
                <h2 class="text-lg font-semibold mb-4">{{ column.title }}
                    <span class="text-sm font-semibold text-gray-600 ml-3 my-auto border rounded-full p-1"> {{
                        column.tasks.length }}</span>
                    <hr :class="[column.color, 'border-b font-bold my-2']" />
                </h2>
                <div class="h-full rounded-lg " @drop="addTaskToColumn(index)" @dragover.prevent>
                    <div v-for="task in column.tasks" :key="task.id" class="p-2 mb-2 bg-yellow-50 rounded-md cursor-pointer"
                        draggable="true" @dragstart="dragstart(task, index)">
                        <div>
                            <span :class="[task.bgColor, 'p-1 mr-2 rounded-l-md text-sm font-medium text-white']">Task:{{
                                task.id }} </span>
                            <span class="text-sm text-gray-400">{{ task.description }}</span>
                        </div>
                    </div>
                </div>
            </div>
        </div>

        <!-- ADDING TASK BUTTON -->
        <div class="mt-4">
            <button @click="showAddTaskModal = true"
                class="bg-pink-400 hover:bg-pink-300 font-bold text-white px-4 py-2 rounded-md">Add New
                Task</button>
        </div>
        <NewTask :columns="columns" :show="showAddTaskModal" @close="showAddTaskModal = false" @add-task="handleAddTask" />
    </div>
</template>
  
<script setup>
import { ref } from 'vue';
import NewTask from './NewTask.vue';

const columns = ref([
    {
        title: 'To Do', tasks: [
            { id: 1, name: 'Plan', description: 'Lorem ipsum dolor, sit amet consectetur adipisicingelit.', bgColor: 'bg-pink-600' },
            { id: 2, name: 'code', description: 'Lorem ipsum dolor, sit amet consectetur adipisicingelit.', bgColor: 'bg-purple-400' },
        ],
        color: 'border-black',
    },
    {
        title: 'In Progress', tasks: [
            { id: 5, name: 'Design', description: 'Lorem ipsum dolor, sit amet consectetur adipisicingelit.', bgColor: 'bg-green-500' },
            { id: 6, name: 'test', description: 'Lorem ipsum dolor, sit amet consectetur adipisicingelit.', bgColor: 'bg-blue-500' },
        ],
        color: 'border-blue-600',
    },
    {
        title: 'QA', tasks: [
            { id: 3, name: 'Add', initials: 'C', href: '#', members: 16, description: 'Lorem ipsum dolor, sit amet consectetur adipisicingelit.', bgColor: 'bg-yellow-500' },
            { id: 7, name: 'review', initials: 'F', href: '#', members: 8, description: 'Lorem ipsum dolor, sit amet consectetur adipisicingelit.', bgColor: 'bg-purple-700' },
        ],
        color: 'border-yellow-500',
    },
    {
        title: 'Complete', tasks: [{ id: 8, name: 'search', description: 'Lorem ipsum dolor, sit amet consectetur adipisicingelit.', bgColor: 'bg-red-900' }],
        color: 'border-green-500',
    },
]);

const dragItem = ref(null);
const showAddTaskModal = ref(false);

const dragstart = (task, columnIndex) => {
    dragItem.value = { task, columnIndex };
};

const addTaskToColumn = (targetColumnIndex) => {
    const { task, columnIndex } = dragItem.value;
    if (columnIndex !== targetColumnIndex && targetColumnIndex !== null) {
        const fromColumn = columns.value[columnIndex];
        const toColumn = columns.value[targetColumnIndex];
        if (fromColumn && toColumn) {
            fromColumn.tasks = fromColumn.tasks.filter(t => t.id !== task.id);
            toColumn.tasks.push(task);
        }
    }
};

const handleAddTask = (newTask) => {
    columns.value[newTask.columnIndex].tasks.push(newTask.task);
};
</script>
  
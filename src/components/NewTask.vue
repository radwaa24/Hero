<template>
    <div v-if="show" class="fixed inset-0 z-10 overflow-y-auto">
        <div class="flex items-center justify-center min-h-screen pt-4 px-4 pb-20 text-center ">
            <div class="fixed inset-0 transition-opacity" aria-hidden="true">
                <div class="absolute inset-0 bg-gray-100 opacity-75"></div>
            </div>
            <div class="inline-block rounded-lg  shadow-xl transform transition-all  mx-auto max-w-lg w-full">
                <div class="bg-white rounded-lg shadow-xl p-5">
                    <div class="">
                        <div class=" text-center  ">
                            <h3 class="text-lg font-bold leading-6 text-gray-950">Add New Task</h3>
                            <div class="mt-2">
                                <div class="mb-4">
                                    <input v-model="newTaskName" type="text"
                                        class="border-gray-100 shadow-sm border rounded-md p-2 w-full"
                                        placeholder="Task Name">
                                </div>
                                <div>
                                    <textarea v-model="newTaskDescription"
                                        class="border-gray-100 shadow-sm border rounded-md p-2 w-full"
                                        placeholder="Task Description"></textarea>
                                </div>
                                <div class="mt-4">
                                    <select v-model="selectedColumn"
                                        class="border-gray-100 shadow-sm border rounded-md p-2 w-full">
                                        <option value="" class="font-bold">Where to Add?</option>
                                        <option v-for="(column, index) in columns" :key="index" :value="index">{{
                                            column.title }}</option>
                                    </select>
                                </div>
                            </div>
                        </div>
                    </div>
                    <div class=" my-2">
                        <button @click="addNewTask" :disabled="!newTaskName || !newTaskDescription || selectedColumn === ''"
                            type="button"
                            class=" inline-flex justify-center rounded-md border border-transparent shadow-sm px-4 py-2 bg-pink-400 font-semibold text-white hover:bg-pink-300 ">
                            Add Task
                        </button>
                        <button @click="closeModal" type="button"
                            class=" mx-2 inline-flex justify-center rounded-md border  shadow-sm px-4 py-2  font-semibold hover:bg-gray-200">
                            Cancel
                        </button>
                    </div>
                </div>

            </div>
        </div>
    </div>
</template>
  
<script setup>
import { ref } from 'vue';

const props = defineProps({
    columns: Array,
    show: Boolean,
});

const emit = defineEmits(['add-task', 'close']);

const newTaskName = ref('');
const newTaskDescription = ref('');
const selectedColumn = ref('');

const addNewTask = () => {
    const columnIndex = parseInt(selectedColumn.value);
    const newTask = {
        id: generateUniqueId(),
        name: newTaskName.value,
        description: newTaskDescription.value,
        initials: 'New',
        href: '#',
        members: 1,
        bgColor: 'bg-gray-400',
    };
    emit('add-task', { task: newTask, columnIndex });
    newTaskName.value = '';
    newTaskDescription.value = '';
    selectedColumn.value = '';
    emit('close');
};

const closeModal = () => {
    emit('close');
};

const generateUniqueId = () => {
    return '_' + Math.random().toString(36).substr(2, 9);
};
</script>
  
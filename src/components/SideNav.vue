<template>
    <div class="hidden lg:fixed lg:inset-y-0 lg:z-50 lg:flex lg:w-72 lg:flex-col">
        <div class="flex grow flex-col gap-y-5  h-full border-r border-gray-200 bg-white px-6 pb-4">
            <div>
                <img class=" w-24" src="https://thumbs.dreamstime.com/b/word-hero-typewriter-white-background-91522314.jpg"
                    alt="Your Company" />
            </div>
            <nav class="flex flex-1 flex-col">
                <ul role="list" class="flex flex-1 flex-col gap-y-7">
                    <li>
                        <ul role="list" class="-mx-2 space-y-1">
                            <li v-for="item in navigation" :key="item.name">
                                <a :href="item.href"
                                    :class="[item.current ? 'bg-gray-50 text-pink-400' : 'text-gray-700 hover:text-pink-400 hover:bg-gray-50', 'group flex gap-x-3 rounded-md p-2 text-sm leading-6 font-semibold']">
                                    <component :is="item.icon"
                                        :class="[item.current ? 'text-pink-400' : 'text-gray-400 group-hover:text-pink-400', 'h-6 w-6 shrink-0']"
                                        aria-hidden="true" />
                                    {{ item.name }}
                                </a>
                            </li>
                        </ul>
                    </li>
                    <li>
                        <div class="text-xs font-semibold leading-6 text-gray-400">WorkSpace</div>
                        <ul role="list" class="-mx-2 mt-2 space-y-1">
                            <li v-for="item in workSpaces" :key="item.name">
                                <a :href="item.href"
                                    :class="[item.current ? 'bg-gray-50 text-pink-400' : 'text-gray-700 hover:text-pink-400 hover:bg-gray-50', 'group flex gap-x-3 rounded-md p-2 text-sm leading-6 font-semibold']">
                                    <span
                                        :class="[item.current ? 'text-pink-400 border-pink-400' : 'text-gray-400 border-gray-200 group-hover:border-pink-400 group-hover:text-pink-400', 'flex h-6 w-6 shrink-0 items-center justify-center rounded-lg border text-[0.625rem] font-medium bg-white']">{{
                                            item.initial }}</span>
                                    <span class="truncate">{{ item.name }}</span>
                                </a>
                            </li>
                        </ul>
                    </li>
                    <li class="">
                        <a href="#"
                            class="group -mx-2 flex gap-x-3 rounded-md p-2 text-sm font-semibold leading-6 text-gray-700 hover:bg-gray-50 hover:text-pink-400">
                            <Cog6ToothIcon class="h-6 w-6 shrink-0 text-gray-400 group-hover:text-pink-400"
                                aria-hidden="true" />
                            Settings
                        </a>
                    </li>
                </ul>
            </nav>
        </div>
    </div>
</template>
<script setup>
import { ref } from 'vue'

const sidebarOpen = ref(false)



import {

    UsersIcon,
    Cog6ToothIcon,
    FolderIcon,
    DocumentIcon,
    HomeIcon,
    Bars3Icon
} from '@heroicons/vue/24/outline'

const navigation = [
    { name: 'Home', href: '#', icon: HomeIcon },
    { name: 'My Tasks', href: '#', icon: DocumentIcon, },
    { name: 'Goals', href: '#', icon: FolderIcon, },
    { name: 'Members', href: '#', icon: UsersIcon, },
]
const workSpaces = [
    { id: 1, name: 'Hikoko Design', href: '#', initial: 'H', current: false },
    { id: 2, name: 'Website Design ', href: '#', initial: 'W', current: false },
    { id: 3, name: 'Mobile Design', href: '#', initial: 'M', current: false },
]
</script>
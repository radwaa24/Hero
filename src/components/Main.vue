<template>
    <div>
        <SideNav />

        <div class="lg:ml-72">
            <div>
                <Nav />
            </div>
            <main class="py-10">
                <div class="px-4 ">
                    <Dashboard />
                </div>
            </main>
        </div>
    </div>
</template>
  
<script setup>
import Dashboard from './Dashboard.vue'
import Nav from './Nav.vue'
import SideNav from './SideNav.vue'



</script>
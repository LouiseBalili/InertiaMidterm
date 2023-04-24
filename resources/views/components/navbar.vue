<script setup>
import {onMounted} from 'vue'
import { Link } from '@inertiajs/inertia-vue3'
import { defineProps } from 'vue'
defineProps({
    user: ''
})

onMounted(() => {
    const menu = document.getElementById('navbar-solid-bg')
    const btn = document.getElementById('toggle-btn')

    btn.addEventListener('click', () => {
        if(menu.style.display == 'none') {
            menu.style.display = 'block'
        }else{
            menu.style.display = 'none'
        }
    })
})
</script>

<template>

<nav class="bg-gray-50 border-8 border-gray-800 px-2 sm:px-4 py-2.5 rounded bg-gray-900">
    <div class="mx-auto flex justify-between items-center p-3">
        <div class="flex items-center">
            <Link href="/home" class="self-center text-xl font-semibold whitespace-nowrap text-gray-400">InertiaJS</Link>
        </div>

        <ul class="md:flex md:items-center">
          <li v-if="user" class="mx-3">
            <Link href="/home" class="block py-2 pl-3 pr-4 text-gray-400 rounded hover:bg-gray-100 md:hover:bg-transparent md:hover:text-blue-700 md:p-0 text-gray-400">Home</Link>
          </li>
          <li v-if="user" class="mx-3">
            <Link href="/members" class="block py-2 pl-3 pr-4 text-gray-400 rounded hover:bg-gray-100 md:hover:bg-transparent md:hover:text-blue-700 md:p-0 text-gray-400">Members</Link>
          </li>
          <li v-if="user" class="mx-3">
            <Link href="/companies" class="block py-2 pl-3 pr-4 text-gray-400 rounded hover:bg-gray-100 md:hover:bg-transparent md:hover:text-blue-700 md:p-0 text-gray-400">Companies</Link>
          </li>
        </ul>

        <div class="flex items-center">
            <Link v-if="!user" href="/signup" class="text-sm px-4 py-3 text-white bg-gray-600 focus:ring-4 focus:outline-none focus:ring-primary-300 font-medium rounded-lg" style="margin-right: 5px;">Register</Link>
            <Link v-if="!user" href="/" class="text-sm px-4 py-3 text-white bg-blue-600 focus:ring-4 focus:outline-none focus:ring-primary-300 font-medium rounded-lg">Login</Link>
            <p v-if="user" class="text-sm mr-6 text-gray-400">You are logged in as: &nbsp; <i class="fa-solid fa-user"></i> <strong>{{ user.username }}</strong></p>

            <Link v-if="user" href="/logout" class="text-sm px-3.5 py-1.5 bg-blue-600 text-white rounded-lg">Logout</Link>
        </div>
    </div>
  </nav>

</template>

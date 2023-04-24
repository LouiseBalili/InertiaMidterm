<script setup>
import {Link} from '@inertiajs/inertia-vue3'

defineProps({
    'companies': Array
})

const closeNotif = () => {
    const toast = document.getElementById('toast-bottom-left');
    toast.style.opacity = '0'
    toast.style.transition = '.5s all ease'
}
</script>

<template layout="default">
    <div class="container-md mx-auto p-8">
        <div class="flex items-center mb-4 text-center ml-80">
            <h1 class="text-4xl text-gray-300 mb-5 ml-40">List of Companies</h1>
            <Link href="/companies/create" class="text-gray-300 ml-20 mb-4 rounded-lg border-2 border-solid hover:border-gray-400 hover:bg-gray-600 hover:text-gray-300 px-4 py-2">+ Add Company</Link>
        </div>

        <table class="w-full text-sm text-left text-gray-400">
            <thead class="text-xs uppercase bg-gray-700 text-gray-400">
                <tr>
                    <th scope="col" class="px-6 py-5">
                        #
                    </th>
                    <th scope="col" class="px-6 py-5">
                        Company name
                    </th>
                    <th scope="col" class="px-6 py-5">
                        Type
                    </th>
                    <th scope="col" class="px-6 py-5">
                        Address
                    </th>
                    <th scope="col" class="px-6 py-5">
                        Net Worth
                    </th>
                    <th scope="col" class="px-6 py-5 text-center">
                        ...
                    </th>
                </tr>
            </thead>
            <tbody v-for="company of companies" :key="company.id">
                <tr class="border-b bg-gray-800 border-gray-700 hover:bg-gray-600">
                    <td class="px-6 py-6">
                        {{ company.id }}
                    </td>
                    <td class="px-6 py-6">
                        {{ company.name }}
                    </td>
                    <td class="px-6 py-6">
                        {{ company.type }}
                    </td>
                    <td class="px-6 py-6">
                        {{ company.address }}
                    </td>
                    <td class="px-6 py-6">
                        {{ company.net_worth }}
                    </td>
                    <td class="px-6 py-6">
                        <Link :href="'/companies/edit/' + company.id" class=""><i class="fa-solid fa-pen"></i></Link>
                    </td>
                </tr>
            </tbody>
        </table>

        <div v-if="$page.props.flash.message" id="toast-bottom-left" class="transition-ease fixed flex justify-between items-center w-full max-w-xs p-4 space-x-4 text-gray-500 bg-green-50 rounded-md shadow bottom-14 left-14 border-l-8 border border-green-400" role="alert">
            <div class="flex items-center">
                <a href="#" class="text-green-500"><i class="fa-solid fa-circle-check"></i></a>
                <div class="pl-4 border-l-2 border-green-600 text-green-700 text-sm font-normal ml-4">{{ $page.props.flash.message }}</div>
            </div>

            <button id="close-button" @click="closeNotif()"><i class="fa-solid fa-xmark"></i></button>
        </div>
    </div>
</template>


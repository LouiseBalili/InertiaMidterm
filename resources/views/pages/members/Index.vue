<script setup>
import {Link} from '@inertiajs/inertia-vue3'

defineProps({
    'members': Array
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
            <h1 class="text-4xl text-gray-300 mb-5 ml-40">List of Members</h1>
            <Link href="/members/create" class="text-gray-300 ml-20 mb-4 rounded-lg border-2 border-solid hover:border-gray-400 hover:bg-gray-600 hover:text-gray-300 px-4 py-2"> + Add Member</Link>
        </div>

        <table class="w-full text-sm text-left text-gray-400">
            <thead class="text-xs uppercase bg-gray-700 text-gray-400">
                <tr>
                    <th scope="col" class="px-6 py-5">
                        #
                    </th>
                    <th scope="col" class="px-6 py-5">
                        Last Name
                    </th>
                    <th scope="col" class="px-6 py-5">
                        First Name
                    </th>
                    <th scope="col" class="px-6 py-5">
                        Designation
                    </th>
                    <th scope="col" class="px-6 py-5">
                        Company
                    </th>
                    <th scope="col" class="px-6 py-5 text-center">
                        ...
                    </th>
                </tr>
            </thead>
            <tbody v-for="member of members" :key="member.id">
                <tr class="border-b bg-gray-800 border-gray-700 hover:bg-gray-600">
                    <td class="px-6 py-6">
                        {{ member.id }}
                    </td>
                    <td class="px-6 py-6">
                        {{ member.last_name }}
                    </td>
                    <td class="px-6 py-6">
                        {{ member.first_name }}
                    </td>
                    <td class="px-6 py-6">
                        {{ member.designation }}
                    </td>
                    <td class="px-6 py-6">
                        {{ member.company.name }}
                    </td>
                    <td class="px-6 py-6 text-center">
                        <Link :href="'/members/edit/' + member.id"><i class="fa-solid fa-pen"></i></Link>
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

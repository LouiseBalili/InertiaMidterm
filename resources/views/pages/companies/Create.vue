<script setup>
import { useForm, Link } from '@inertiajs/inertia-vue3'


let form = useForm({
    name: '',
    type: '',
    address: '',
    net_worth: '',
})

const submit = () => {
    form.post('/companies')

}
</script>

<template>
  <br><br><br>
        <div class="w-1/2 bg-gray-50 rounded-lg shadow dark:border mx-auto md:mt-0 sm:max-w-md xl:p-0 bg-gray-800">
            <div class="p-6 space-y-4 md:space-y-6 sm:p-8">
                <h1 class="text-xl text-center font-bold leading-tight tracking-tight text-gray-300">
                    Add Company
                </h1>
                <form class="space-y-4 md:space-y-6" @submit.prevent="submit">
                    <div>
                        <label for="email" class="block mb-2 text-sm font-medium text-gray-400">Company Name</label>
                        <input v-model="form.name" type="text" class="bg-gray-50 border border-gray-300 text-gray-900 sm:text-sm rounded-lg focus:ring-primary-600 focus:border-primary-600 block w-full p-2.5">
                        <div class="text-sm text-gray-500 italic" v-if="form.errors.name">{{ form.errors.name }}</div>
                    </div>
                    <div>
                        <label for="email" class="block mb-2 text-sm font-medium text-gray-400">Type</label>
                        <input v-model="form.type" type="text" class="bg-gray-50 border border-gray-300 text-gray-900 sm:text-sm rounded-lg focus:ring-primary-600 focus:border-primary-600 block w-full p-2.5">
                        <div class="text-sm text-gray-500 italic" v-if="form.errors.type">{{ form.errors.type }}</div>
                    </div>
                    <div>
                        <label for="text" class="block mb-2 text-sm font-medium text-gray-400">Address</label>
                        <input v-model="form.address" type="text" class="bg-gray-50 border border-gray-300 text-gray-900 sm:text-sm rounded-lg focus:ring-primary-600 focus:border-primary-600 block w-full p-2.5">
                        <div class="text-sm text-gray-500 italic" v-if="form.errors.address">{{ form.errors.address }}</div>
                    </div>
                    <div>
                        <label for="text" class="block mb-2 text-sm font-medium text-gray-400">Net Worth</label>
                        <input v-model="form.net_worth" type="text" class="bg-gray-50 border border-gray-300 text-gray-900 sm:text-sm rounded-lg focus:ring-primary-600 focus:border-primary-600 block w-full p-2.5">
                        <div class="text-sm text-gray-500 italic" v-if="form.errors.net_worth">{{ form.errors.net_worth }}</div>
                    </div>

                    <div class="flex flex-col">
                        <button type="submit" class="w-full text-white bg-blue-600 focus:ring-4 focus:outline-none focus:ring-primary-300 font-medium rounded-lg text-sm px-5 py-2.5 text-center mb-2">Add Company</button>
                        <Link href="/companies" class="w-full text-white bg-gray-500 focus:ring-4 focus:outline-none focus:ring-primary-300 font-medium rounded-lg text-sm px-5 py-2.5 text-center mb-2">Cancel</Link>
                    </div>
                </form>
            </div>
        </div>

</template>

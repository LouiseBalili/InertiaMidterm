<script setup lang="ts">
import NavBar from '../components/navbar.vue'

import { defineProps } from 'vue'
defineProps({
    'auth': Object
})
</script>

<template>
	<NavBar :user="auth.user"></NavBar>

        <slot />
</template>

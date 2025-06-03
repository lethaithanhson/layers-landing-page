<script setup lang="ts">
import { twMerge } from "tailwind-merge"
interface Prop {
    name: string;
    color?: "red" | "blue"
}
withDefaults(defineProps<Prop>(), {
    color: 'blue'
})
</script>

<template>
    <div class="relative">
        <svg xmlns="http://www.w3.org/2000/svg" width="24" height="24" viewBox="0 0 24 24" fill="none"
            stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"
            class="feather feather-mouse-pointer text-white size-5">
            <path d="M3 3l7.07 16.97 2.51-7.39 7.39-2.51L3 3z"></path>
            <path d="M13 13l6 6"></path>
        </svg>
        <div class="absolute top-full left-full">
            <div :class="twMerge('inline-flex rounded-full font-semibold text-sm px-2 rounded-tl-none',
                color === 'red' && 'bg-red-500', color === 'blue' && 'bg-blue-500'
            )">{{ name }}</div>
        </div>
    </div>
</template>

<script setup lang="ts">
import { twMerge } from 'tailwind-merge';



const props = defineProps<{
    title: string,
    description: string
    class?: string
}>()

</script>

<template>
    <div :class="twMerge('bg-neutral-900 border border-white/10 p-6 rounded-3xl', props.class)">
        <div class="aspect-video">
            <slot></slot>
        </div>
        <div class="">
            <h3 class="text-3xl font-medium pt-6">{{ title }}</h3>
            <p class="text-white/50 mt-2">{{ description }}</p>
        </div>
    </div>
</template>

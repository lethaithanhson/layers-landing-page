<script setup lang="ts">
import { twMerge } from 'tailwind-merge';
import type { IntegrationType } from '../@types/types';
import { motion } from "motion-v"


const props = defineProps<{
    integrations: IntegrationType[];
    class?: string;
    reverse?: boolean
}>()
</script>

<template>
    <motion.div :animate="{ y: reverse ? 0 : '-50%' }" :initial="{ y: reverse ? '-50%' : 0 }"
        :transition="{ duration: 30, repeat: Infinity, ease: 'linear' }"
        :class="twMerge('flex flex-col gap-4 pb-4', props.class)">
        <template v-for="(_, index) in 2" :key="index">
            <div class="bg-neutral-900 border border-white/10 rounded-3xl p-6" v-for="integration in integrations"
                :key="integration.name">
                <div class="flex justify-center">
                    <img :src="integration.icon" :alt="integration.name" class="size-24">
                </div>
                <h3 class="text-3xl text-center mt-6">{{ integration.name }}</h3>
                <p class="text-center text-white/50 mt-2">{{ integration.description }}</p>
            </div>
        </template>

    </motion.div>
</template>

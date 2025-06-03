<script setup lang="ts">
import { motion, useAnimate, type AnimationPlaybackControlsWithThen } from 'motion-v'
import { onMounted, ref, watch } from 'vue';

const [scope, animate] = useAnimate()
const animation = ref<AnimationPlaybackControlsWithThen | null>(null)
const isHover = ref(false)

onMounted(() => {
    animation.value = animate(scope.value, { x: '-50%' }, { duration: 30, ease: 'linear', repeat: Infinity })
})

watch(isHover, () => {
    if (animation.value) {
        if (isHover.value) {
            animation.value.speed = 0.5
        } else {
            animation.value.speed = 1
        }
    }
})

</script>

<template>
    <section class="py-24">
        <div class="overflow-x-clip p-4 flex">
            <motion.div ref="scope"
                class="flex flex-none gap-16 pr-16 text-7xl md:text-8xl font-medium group cursor-pointer"
                @mouseenter="isHover = true" @mouseleave="isHover = false">
                <div v-for="(_, index) in Array.from({ length: 10 })" :key="index" class="flex items-center gap-16">
                    <span class="text-lime-400 text-7xl">&#10038;</span>
                    <span class="group-hover:text-lime-400">Try it for free</span>
                </div>
            </motion.div>
        </div>
    </section>
</template>
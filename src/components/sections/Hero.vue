<script setup lang="ts">
import Button from "../ui/Button.vue";
import designExmaple1 from "../../assets/images/design-example-1.png"
import designExmaple2 from "../../assets/images/design-example-2.png"
import cursorYouImage from "../../assets/images/cursor-you.png"
import Pointer from "../ui/Pointer.vue";
import { motion, useAnimate } from "motion-v"
import { onMounted } from "vue";


const [leftDesignScope, leftDesignAnimate] = useAnimate()
const [leftPointerScope, leftPointerAnimate] = useAnimate()

const [rightDesignScope, rightDesignAnimate] = useAnimate()
const [rightPointerScope, rightPointerAnimate] = useAnimate()



onMounted(() => {

    leftDesignAnimate([
        // [leftDesignScope.value, { opacity: 1 }, { duration: 0.5 }],
        // [leftDesignScope.value, { x: 0, y: 0 }, { duration: 0.5 }],
        [leftDesignScope.value, { opacity: 0, y: 100, x: -100 }, { duration: 0 }],
        [leftDesignScope.value, { opacity: 1, y: 0, x: 0 }, { duration: 0.5 }],
    ])
    leftPointerAnimate([
        [leftPointerScope.value, { opacity: 1 }, { duration: 0.5 }],
        [leftPointerScope.value, { x: -100, y: 0 }, { duration: 0.5 }],
        [leftPointerScope.value, { x: 0, y: [0, 16, 0] }, { duration: 0.5, ease: 'easeInOut' }],
    ])

    rightDesignAnimate([
        // [rightDesignScope.value, { opacity: 1 }, { duration: 0.5, delay: 1.5 }],
        // [rightDesignScope.value, { x: 0, y: 0 }, { duration: 0.5 }],
        [rightDesignScope.value, { opacity: 0, y: 100, x: 100 }, { duration: 0 }],
        [rightDesignScope.value, { opacity: 1, y: 0, x: 0 }, { duration: 0.5, delay: 1.5 }],
    ])

    rightPointerAnimate([
        [rightPointerScope.value, { opacity: 1 }, { duration: 0.5, delay: 1.5 }],
        [rightPointerScope.value, { x: 175, y: 0 }, { duration: 0.5 }],
        [rightPointerScope.value, { x: 0, y: [0, 20, 0] }, { duration: 0.5, ease: 'easeInOut' }],
    ])
})

</script>

<template>
    <section id="hero" class="py-24 overflow-x-clip relative scroll-mt-[86px] md:pb-[98px] lg:scroll-mt-[130px]"
        :style="{ cursor: `url(${cursorYouImage}), auto` }">
        <div class="container relative">
            <motion.div ref="leftDesignScope" drag class="absolute -left-32 top-16 hidden lg:block">
                <img draggable="false" :src="designExmaple1" alt="Design Example" />
            </motion.div>
            <motion.div ref="leftPointerScope" :initial="{ opacity: 0, y: 100, x: -200 }"
                class="absolute left-56 top-96 hidden lg:block">
                <Pointer name="Andrea" />
            </motion.div>

            <motion.div ref="rightDesignScope" drag class="absolute -right-64 -top-16 hidden lg:block">
                <img draggable="false" :src="designExmaple2" alt="Design Example" />
            </motion.div>
            <motion.div ref="rightPointerScope" :initial="{ opacity: 0, y: 100, x: 275 }"
                class="absolute right-80 -top-4 hidden lg:block">
                <Pointer name="Bryan" color="red" />
            </motion.div>
            <div class="flex justify-center">
                <div
                    class="inline-flex py-1 px-3 bg-gradient-to-r from-purple-400 to-pink-400 rounded-full text-neutral-950 font-semibold">
                    ✨ $7.5M seed round raised
                </div>
            </div>
            <h1 class="text-6xl font-medium text-center mt-6 md:text-7xl lg:text-8xl max-w-4xl mx-auto">Impactful
                design, created
                effortlessly</h1>
            <p class="text-center text-xl text-white/50 mt-8 max-w-2xl mx-auto">Design tools shouldn't slow you down.
                Layers
                combines
                powerful features with an intuitive
                interface that keeps you in your creative flow.</p>
            <form class="flex border border-white/15 rounded-full p-2 mt-8 md:max-w-lg mx-auto">
                <input class="bg-transparent px-4 grow w-full focus:outline-0" type="email"
                    placeholder="Enter your email">
                <Button size="sm" class="shrink-0" type="submit">Sign Up</Button>
            </form>
        </div>
    </section>
</template>
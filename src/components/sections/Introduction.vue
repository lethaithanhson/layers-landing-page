<script setup lang="ts">
import { onMounted, ref } from "vue";
import Tag from "../ui/Tag.vue"
import { useScroll, useTransform } from "motion-v"
import { twMerge } from "tailwind-merge";


const text = `You're racing to create exceptional work, but traditional design tools slow you down with unnecessary complexity and steep learning curves.`;
const words = text.split(" ")

const scrollTarget = ref(null)
const currentWord = ref(0)

const { scrollYProgress } = useScroll({ target: scrollTarget, offset: ['start end', "end end"] })
const wordIndex = useTransform(scrollYProgress, [0, 1], [0, words.length])

onMounted(() => {
    scrollYProgress.on("change", (value) => {
        console.log("scrollYProgress:", value); // Debug giá trị scrollYProgress
    });
    wordIndex.on("change", (latest) => {
        console.log({ latest });

        currentWord.value = latest; // Làm tròn để lấy chỉ số nguyên
    });
});


</script>
<template>
    <section class="py-28 lg:py-40">
        <div class="container">
            <div class="sticky top-20 md:top-28 lg:top-40">
                <div class="flex justify-center">
                    <Tag>Introduction Layers</Tag>
                </div>
                <div class="text-4xl md:text-6xl lg:text-7xl text-center font-medium mt-10">
                    <span class="">Your creative process deserve better.</span>{{ " " }}
                    <span class="text-white/15">
                        <span :class="twMerge('transition', index < currentWord && 'text-white')"
                            v-for="(word, index) in words" :key="index">
                            {{ `${word} ` }}
                        </span>
                    </span>
                    <span class="text-lime-400 block">That's why we build Layers.</span>
                </div>
            </div>
            <div class="h-[300vh]" ref="scrollTarget"></div>
        </div>
    </section>
</template>
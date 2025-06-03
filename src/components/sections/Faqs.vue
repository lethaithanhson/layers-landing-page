<script setup lang="ts">
import { twMerge } from 'tailwind-merge';
import Tag from '../ui/Tag.vue'
import { ref } from 'vue';
import { AnimatePresence, motion } from 'motion-v';

const faqs = [
    {
        question: "How is Layers different from other design tools?",
        answer: "Unlike traditional design tools, Layers prioritizes speed and simplicity without sacrificing power. Our intelligent interface adapts to your workflow, reducing clicks and keeping you in your creative flow.",
    },
    {
        question: "Is there a learning curve?",
        answer: "Layers is designed to feel intuitive from day one. Most designers are productive within hours, not weeks. We also provide interactive tutorials and comprehensive documentation to help you get started.",
    },
    {
        question: "How do you handle version control?",
        answer: "Every change in Layers is automatically saved and versioned. You can review history, restore previous versions, and create named versions for important milestones.",
    },
    {
        question: "Can I work offline?",
        answer: "Yes! Layers includes a robust offline mode. Changes sync automatically when you're back online, so you can keep working anywhere.",
    },
    {
        question: "How does Layers handle collaboration?",
        answer: "Layers is built for collaboration. You can invite team members to your projects, share feedback, and work together in real-time.",
    },
];

const selectedIndex = ref(0)
</script>

<template>
    <section id="faqs" class="py-24 scroll-mt-2.5">
        <div class="container">
            <div class="flex justify-center">
                <Tag>Faqs</Tag>
            </div>
            <h2 class="text-6xl font-medium mt-6 text-center max-w-xl mx-auto">Questions? We've got <span
                    class="text-lime-400">answers</span></h2>
            <div class="mt-12 flex flex-col gap-6 max-w-xl mx-auto">
                <div class="bg-neutral-900 rounded-2xl border border-white/10 p-6" v-for="(faq, faqIndex) in faqs"
                    :key="faq.question">
                    <div class="flex justify-between items-center cursor-pointer" role="button"
                        @click="selectedIndex = faqIndex">
                        <h3 class="font-medium">{{ faq.question }}</h3>
                        <svg xmlns="http://www.w3.org/2000/svg" width="24" height="24" viewBox="0 0 24 24" fill="none"
                            stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"
                            :class="twMerge('feather feather-plus text-lime-400 shrink-0 transition duration-300', faqIndex === selectedIndex && 'rotate-45')">
                            <line x1="12" y1="5" x2="12" y2="19"></line>
                            <line x1="5" y1="12" x2="19" y2="12"></line>
                        </svg>
                    </div>
                    <AnimatePresence>
                        <motion.div :initial="{ height: 0, marginTop: 0 }" :animate="{ height: 'auto', marginTop: 24 }"
                            :exit="{ height: 0, marginTop: 0 }" v-if="selectedIndex === faqIndex"
                            class="overflow-hidden">
                            <p class="text-white/50">{{ faq.answer }}</p>
                        </motion.div>
                    </AnimatePresence>
                </div>
            </div>
        </div>
    </section>
</template>
<script setup lang="ts">
import { onMounted, onUnmounted, ref } from "vue";
import logoImage from "../../assets/images/logo.svg"
import Button from "../ui/Button.vue";
import { twMerge } from "tailwind-merge";
import { AnimatePresence, motion } from "motion-v";

const navLinks = [
    { label: "Home", id: "hero" },
    { label: "Features", id: "features" },
    { label: "Integrations", id: "integrations" },
    { label: "FAQs", id: "faqs" },
]

const isOpen = ref(false)
const activeId = ref("");

const scrollToSection = (id: string) => {
    if (id === '#') {
        window.scrollTo({ top: 0, behavior: 'smooth' })
    }
    const element = document.getElementById(id);
    if (element) {
        element.scrollIntoView({ behavior: "smooth", block: "start" });
    }
};

onMounted(() => {
    const observer = new IntersectionObserver(
        (entries) => {
            entries.forEach((entry) => {
                if (entry.isIntersecting) activeId.value = entry.target.id;
            });
        },
        { rootMargin: "-80px 0px 0px 0px", threshold: 0.1 }
    );

    navLinks.forEach((section) => {
        const element = document.getElementById(section.id);
        if (element) observer.observe(element);
    });

    onUnmounted(() => {
        navLinks.forEach((section) => {
            const element = document.getElementById(section.id);
            if (element) observer.unobserve(element);
        });
    });
});

</script>

<template>
    <section class="py-4 lg:py-8 fixed w-full top-0 z-50">
        <div class="container max-w-5xl mx-auto">
            <div class="border border-white/15 rounded-[27px] md:rounded-full bg-neutral-950/70 backdrop-blur">
                <div class="grid grid-cols-2 lg:grid-cols-3 p-2 md:pr-2 px-4 items-center">
                    <div @click="scrollToSection('hero')" class="cursor-pointer">
                        <img :src="logoImage" alt="Layers logo" class="h-9 md:h-auto w-auto" />
                    </div>
                    <div class="lg:flex justify-center items-center hidden">
                        <nav class="flex gap-6 font-medium">
                            <a v-for="navLink in navLinks" :key="navLink.label" href="javascript:void(0)"
                                @click="scrollToSection(navLink.id)"
                                :class="twMerge('hover:text-lime-400 duration-300', activeId === navLink.id && 'text-lime-500')">{{
                                    navLink.label }}</a>
                        </nav>
                    </div>
                    <div class="flex justify-end gap-4">
                        <svg xmlns="http://www.w3.org/2000/svg" width="24" height="24" viewBox="0 0 24 24" fill="none"
                            stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"
                            class="feather feather-menu md:hidden" @click="isOpen = !isOpen">
                            <line x1="3" y1="12" x2="21" y2="12" :class="twMerge('transition', isOpen && 'opacity-0')">
                            </line>
                            <line x1="3" y1="6" x2="21" y2="6"
                                :class="twMerge('origin-left transition', isOpen && 'rotate-45 -translate-y-1')">
                            </line>
                            <line x1="3" y1="18" x2="21" y2="18"
                                :class="twMerge('origin-left transition', isOpen && '-rotate-45 translate-y-1')">
                            </line>
                        </svg>
                        <Button variant="secondary" class="hidden md:inline-flex items-center">
                            Log In
                        </Button>
                        <Button class="hidden md:inline-flex items-center">
                            Sign Up
                        </Button>
                    </div>
                </div>
                <AnimatePresence>
                    <motion.div :initial="{ height: 0 }" :animate="{ height: 'auto' }" :exit="{ height: 0 }"
                        v-if="isOpen" class="overflow-y-hidden">
                        <div class="flex flex-col items-center gap-4 py-2 ">
                            <a href="javascript:void(0)" class="" @click="scrollToSection(item.id)"
                                v-for="(item, index) in navLinks" :key="index">
                                {{ item.label }}
                            </a>
                            <Button size="sm" variant="secondary">
                                Log In
                            </Button>
                            <Button size="sm">
                                Sign Up
                            </Button>
                        </div>
                    </motion.div>
                </AnimatePresence>
            </div>
        </div>
    </section>
    <div class="pb-[86px] md:pb-[98px] lg:pb-[130px]"></div>
</template>

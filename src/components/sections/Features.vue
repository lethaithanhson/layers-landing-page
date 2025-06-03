<script setup lang="ts">
import FeatureCard from "../FeatureCard.vue";
import Tag from "../ui/Tag.vue"
import avatar1 from "../../assets/images/avatar-ashwin-santiago.jpg"
import avatar2 from "../../assets/images/avatar-lula-meyers.jpg"
import avatar3 from "../../assets/images/avatar-florence-shaw.jpg"
import avatar4 from "../../assets/images/avatar-owen-garcia.jpg"
import incredibleGif from "../../assets/images/gif-incredible.mp4"
import Avatar from "../ui/Avatar.vue";


const features = [
    "Asset Library",
    "Code Preview",
    "Flow Mode",
    "Smart Sync",
    "Auto Layout",
    "Fast Search",
    "Smart Guides",
];
</script>

<template>
    <section id="features" class="py-24 scroll-mt-2.5">
        <div class="container">
            <div class="flex justify-center">
                <Tag>Features</Tag>
            </div>
            <h2 class="text-6xl font-medium text-center mt-6 max-w-2xl mx-auto">
                Where power meets <span class="text-lime-400">simplicity</span>
            </h2>
            <div class="mt-12 grid grid-cols-1 md:grid-cols-4 lg:grid-cols-3 gap-8">
                <FeatureCard class="md:col-span-2 lg:col-span-1 group" title="Real-time Collaboration"
                    description="Work together seamlessly with conflict-free team editing">
                    <div class="aspect-video flex items-center justify-center">
                        <Avatar class="z-40">
                            <img :src="avatar1" alt="Avatar 1" class="rounded-full">
                        </Avatar>
                        <Avatar class="-ml-6 border-indigo-500 z-30">
                            <img :src="avatar2" alt="Avatar w" class="rounded-full">
                        </Avatar>
                        <Avatar class="-ml-6 !border-amber-500 z-20">
                            <img :src="avatar3" alt="Avatar 3" class="rounded-full">
                        </Avatar>
                        <Avatar class="-ml-6 border-transparent group-hover:border-green-500 transition">
                            <div
                                class="size-full bg-neutral-700 rounded-full flex justify-center items-center gap-1 relative">
                                <img :src="avatar4" alt="Avatar 4"
                                    class="absolute size-full rounded-full opacity-0 group-hover:opacity-100 transition" />
                                <span class="size-1.5 block rounded-full bg-white"></span>
                                <span class="size-1.5 block rounded-full bg-white"></span>
                                <span class="size-1.5 block rounded-full bg-white"></span>
                            </div>
                        </Avatar>
                    </div>
                </FeatureCard>
                <FeatureCard class="md:col-span-2 lg:col-span-1 group" title="Interactive Prototyping"
                    description="Engage your clients with prototypes that react to user actions">
                    <div class="aspect-video flex justify-center items-center">
                        <p
                            class="text-4xl font-extrabold text-white/20 group-hover:text-white/10 duration-500 transition text-center">
                            We’ve achieved
                            <span
                                class="bg-gradient-to-r from-purple-400 to-pink-400 block text-transparent bg-clip-text relative">
                                <span> incredible</span>
                                <video :src="incredibleGif" autoplay loop muted playsinline
                                    class="absolute bottom-full left-1/2 -translate-x-1/2 rounded-2xl shadow-xl opacity-0 pointer-events-none group-hover:opacity-100 transition duration-500"></video>
                            </span>
                            growth this year
                        </p>
                    </div>
                </FeatureCard>
                <FeatureCard class="md:col-span-2 lg:col-span-1 md:col-start-2 lg:col-start-auto group"
                    title="Keyboard Quick Action"
                    description="Powerful commands to help you create designs more quickly">
                    <div class="aspect-video flex justify-center items-center gap-4">
                        <div
                            class="size-14 w-28 bg-neutral-300 inline-flex justify-center items-center rounded-2xl text-xl text-neutral-900 font-medium outline-2 outline-transparent group-hover:outline-lime-400 outline-offset-4 duration-500 transition-all group-hover:translate-y-1">
                            Shift</div>
                        <div
                            class="size-14 bg-neutral-300 inline-flex justify-center items-center rounded-2xl text-xl text-neutral-900 font-medium outline-2 outline-transparent group-hover:outline-lime-400 outline-offset-4 transition-all duration-500 group-hover:translate-y-1 delay-150">
                            Alt</div>
                        <div
                            class="size-14 bg-neutral-300 inline-flex justify-center items-center rounded-2xl text-xl text-neutral-900 font-medium outline-2 outline-transparent group-hover:outline-lime-400 outline-offset-4 transition-all duration-500 group-hover:translate-y-1 delay-300">
                            C</div>
                    </div>
                </FeatureCard>

            </div>

            <div class="mt-8 flex flex-wrap gap-3 justify-center">
                <div class="bg-neutral-900 border border-white/10 flex px-3 md:px-5 py-1.5 md:py-2 items-center gap-3 rounded-2xl hover:scale-105 transition duration-500 group cursor-default"
                    v-for="feature in features" :key="feature">
                    <span
                        class="bg-lime-400 text-neutral-950 size-5 rounded-full flex items-center justify-center text-xl group-hover:rotate-45 transition duration-500">&#10038;</span>
                    <span class="font-medium md:text-lg">{{ feature }}</span>
                </div>
            </div>
        </div>
    </section>
</template>
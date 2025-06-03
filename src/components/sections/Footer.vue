<script setup lang="ts">

import logoImage from "../../assets/images/logo.svg"

const footerLinks = [
    { href: "#", label: "Contact" },
    { href: "#", label: "Privacy Policy" },
    { href: "#", label: "Terms & Conditions" },
];
</script>

<template>
    <footer class="py-16 md:py-6">
        <div class="container">
            <div class="flex flex-col md:flex-row md:justify-between items-center gap-6">
                <div class="">
                    <img :src="logoImage" alt="Layers Logo" class="">
                </div>
                <div class="">
                    <nav class="flex gap-6">
                        <a :href="item.href" v-for="(item) in footerLinks" :key="item.label"
                            class="text-white/50 text-sm hover:text-lime-400 duration-300">
                            {{ item.label }}
                        </a>
                    </nav>
                </div>
            </div>
        </div>
    </footer>
</template>
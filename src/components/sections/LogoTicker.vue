<script setup lang="ts">
import quantumLogo from "../../assets/images/quantum.svg";
import acmeLogo from "../../assets/images/acme-corp.svg";
import echoValleyLogo from "../../assets/images/echo-valley.svg";
import pulseLogo from "../../assets/images/pulse.svg";
import outsideLogo from "../../assets/images/outside.svg";
import apexLogo from "../../assets/images/apex.svg";
import celestialLogo from "../../assets/images/celestial.svg";
import twiceLogo from "../../assets/images/twice.svg";
import { motion } from "motion-v"

const logos = [
    { name: "Quantum", image: quantumLogo },
    { name: "Acme Corp", image: acmeLogo },
    { name: "Echo Valley", image: echoValleyLogo },
    { name: "Pulse", image: pulseLogo },
    { name: "Outside", image: outsideLogo },
    { name: "Apex", image: apexLogo },
    { name: "Celestial", image: celestialLogo },
    { name: "Twice", image: twiceLogo },
];
</script>
<template>
    <section class="py-24 overflow-x-clip">
        <div class="container">
            <h3 class="text-center text-white/50 text-xl">Already chosen by there market leaders</h3>
            <div
                class="overflow-hidden flex mt-12 [mask-image:linear-gradient(to_right,transparent,black_10%,black_90%,transparent)]">
                <motion.div :animate="{ x: '-50%' }" :transition="{ duration: 30, ease: 'linear', repeat: Infinity }"
                    class="flex flex-none gap-24 pr-24">
                    <template v-for="(_, index) in 2" :key="index">
                        <img v-for="logo in logos" :key="logo.name" :src="logo.image" :alt="logo.name" />
                    </template>
                </motion.div>
            </div>
        </div>
    </section>
</template>
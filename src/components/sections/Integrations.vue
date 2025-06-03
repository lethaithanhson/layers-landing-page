<script setup lang="ts">
import Tag from "../ui/Tag.vue"
import figmaIcon from "../../assets/images/figma-logo.svg"
import notionIcon from "../../assets/images/notion-logo.svg"
import slackIcon from "../../assets/images/slack-logo.svg"
import relumeIcon from "../../assets/images/relume-logo.svg"
import framerIcon from "../../assets/images/framer-logo.svg"
import githubIcon from "../../assets/images/github-logo.svg"
import type { IntegrationType } from "../../@types/types"
import IntegrationsColumn from "../IntegrationsColumn.vue"



const integrations: IntegrationType[] = [
    { name: "Figma", icon: figmaIcon, description: "Figma is a collaborative interface design tool." },
    { name: "Notion", icon: notionIcon, description: "Notion is an all-in-one workspace for notes and docs." },
    { name: "Slack", icon: slackIcon, description: "Slack is a powerful team communication platform." },
    { name: "Relume", icon: relumeIcon, description: "Relume is a no-code website builder and design system." },
    { name: "Framer", icon: framerIcon, description: "Framer is a professional website prototyping tool." },
    { name: "GitHub", icon: githubIcon, description: "GitHub is the leading platform for code collaboration." },
];


</script>

<template>
    <section id="integrations" class="py-24 overflow-hidden">
        <div class="container">
            <div class="grid lg:grid-cols-2 items-center lg:gap-16">
                <div>
                    <Tag>Integrations</Tag>
                    <h2 class="text-6xl font-medium mt-6">Plays well with <span class="text-lime-400">others</span></h2>
                    <p class="text-white/50 mt-4 text-lg">Layers seamlessly connects with your favorite tools, making it
                        easy to
                        plug into any workflow and collaborate across platforms.</p>
                </div>
                <!-- <div> -->
                <div
                    class="h-[400px] lg:h-[800px] grid md:grid-cols-2 gap-4 mt-8 lg:mt-0 overflow-hidden [mask-image:linear-gradient(to_bottom,transparent,black_10%,black_90%,transparent)]">
                    <IntegrationsColumn :integrations />
                    <IntegrationsColumn reverse class="hidden md:flex" :integrations="integrations.slice().reverse()" />
                </div>
                <!-- </div> -->
            </div>
        </div>
    </section>
</template>
<script setup lang="ts">
import { cva } from 'class-variance-authority'

const buttonVariants = cva(
    'border rounded-full px-6 font-medium cursor-pointer',
    {
        variants: {
            variant: {
                primary: "bg-lime-400 text-neutral-950 border-lime-400",
                secondary: 'border-white bg-transparent text-white'
            },
            size: {
                default: 'h-12',
                sm: 'h-10'
            },
        },
        defaultVariants: {
            variant: 'primary',
            size: 'default',
        },

    },
)


interface Props {
    variant?: NonNullable<Parameters<typeof buttonVariants>[0]>['variant']
    size?: NonNullable<Parameters<typeof buttonVariants>[0]>['size']
    as?: string
}

withDefaults(defineProps<Props>(), {
    as: 'button',
})
</script>

<template>
    <component :is="as" :class="buttonVariants({ variant, size, class: $attrs.calss ?? '' })">
        <slot></slot>
    </component>
</template>
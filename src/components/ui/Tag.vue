<template>
    <div v-bind="$attrs"
        class="inline-flex border border-lime-400 gap-2 text-lime-400 items-center px-3 py-1 rounded-full uppercase">
        <span>&#10038;</span>
        <span class="text-sm">
            <slot></slot>
        </span>
    </div>
</template>
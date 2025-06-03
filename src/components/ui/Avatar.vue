<script setup lang="ts">

</script>


<template>
    <div v-bind="$attrs" class="size-20 rounded-full overflow-hidden border-4 border-blue-500 p-1 bg-neutral-900">
        <slot></slot>
    </div>
</template>
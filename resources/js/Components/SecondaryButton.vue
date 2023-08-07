<script setup>
defineProps({
    type: {
        type: String,
        default: 'button',
    },
});
</script>

<template>
    <button :type="type" class="rounded-2xl border border-white py-[13px] text-center">
        <slot />
    </button>
</template>

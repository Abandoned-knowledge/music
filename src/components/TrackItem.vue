<template>
    <section class="p-4 w-full flex items-center gap-10 hover:bg-slate-800 transition-all duration-75 cursor-pointer">
        <div class="h-10 w-10 bg-red-500"></div>
        <p>
            <slot name="author"></slot>-<slot name="trackName"></slot>
        </p>
    </section>
</template>

<script setup>

</script>

<style scoped></style>
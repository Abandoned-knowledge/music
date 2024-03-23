<template>
    <section class="p-4 w-full flex items-center gap-10 hover:bg-slate-800 transition-all duration-75 cursor-pointer">
        <img :src="showUrl(props.imageUrl)" class="h-10 w-10 bg-red-500 object-cover"></img>
        <p>
            <slot name="author"></slot> - <slot name="trackName"></slot>
        </p>
    </section>
</template>

<script setup>
const props = defineProps(['imageUrl']);
function showUrl(imgArray) {
    return imgArray.find(item => item.size == 'medium')['#text'];
}
</script>

<style scoped></style>
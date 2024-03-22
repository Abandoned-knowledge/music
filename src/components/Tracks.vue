<template>
    <article class="tracks">
        {{ props.trackList }}
        <button @click="console.log(trackList)">asdasd</button>
        <TrackItem v-for="track in trackList" @click="console.log(tracks)">
            <template #author>Луверанс</template>
            <template #trackName>Душа моя</template>
        </TrackItem>
    </article>
</template>

<script setup>
import TrackItem from "./TrackItem.vue";
const props = defineProps({
    trackList: {
        type: Array,
        required: true
    }
});
</script>

<style scoped>
.tracks {
    @apply overflow-hidden rounded-lg mt-4 absolute top-full w-full border border-slate-600;
}
</style>

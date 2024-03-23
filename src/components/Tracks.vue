<template>
    <article class="tracks" v-show="trackList.length > 0">
        <TrackItem 
        v-for="track in trackList"
        :imageUrl="track.image">
            <template #author>{{ track.name }}</template>
            <template #trackName>{{ track.artist }}</template>
        </TrackItem>
    </article>
</template>

<script setup>
import TrackItem from "./SearchTrackItem.vue";
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

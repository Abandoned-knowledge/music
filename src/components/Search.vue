<script setup>
import SearchIcon from './icons/SearchIcon.vue';
import Tracks from './Tracks.vue';

const APIKEY = "239f65d54aeafe4cc8cc31fc73d235e2";
let modelValue = defineModel();
let tracks = [];

async function searching(value) {

    if (value) {
        let response = await fetch(`http://ws.audioscrobbler.com/2.0/?method=track.search&track=${value}&api_key=${APIKEY}&format=json`);
        let result = await response.json();
        let resultTracks = await result.results.trackmatches.track;
        tracks = resultTracks.slice(0, 5);
    } else {
        tracks = [];
    }
}
</script>

<template>
    <article class="flex items-center relative w-full">

        <SearchIcon class="text-slate-600 w-5 h-5 mr-4 absolute right-0" />

        <input 
        v-model="modelValue"
        @input="searching($event.target.value)" 
        type="text" 
        id="search"
        placeholder="Search . . ."
        class="focus:outline focus:outline-teal-500 rounded-full w-full bg-transparent border border-slate-600 h-fit px-8 py-4">

        <Tracks :trackList="tracks" />
    </article>
</template>

<style scoped>
.tracks {
    @apply overflow-hidden rounded-lg mt-4 absolute top-full w-full border border-slate-600;
}
</style>

<script setup>
import SearchIcon from './icons/SearchIcon.vue';
import Tracks from './Tracks.vue';

const APIKEY = "239f65d54aeafe4cc8cc31fc73d235e2";

let tracks = [];

async function searching(event) {
    let inputValue = event.target.value;
    let response = await fetch(`http://ws.audioscrobbler.com/2.0/?method=track.search&track=${inputValue}&api_key=${APIKEY}&format=json`);
    let result = await response.json();
    let resultTracks = await result.results.trackmatches.track;
    resultTracks.forEach(track => {
        tracks.push(track);
    })
    tracks.length = 5;
}
</script>

<template>
    <article class="flex items-center relative w-full">

        <label for="search" class="absolute right-0">
            <SearchIcon class="text-slate-600 w-5 h-5 mr-4" />
        </label>
        
        <input 
        :value="search" 
        @change="searching($event)" 
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

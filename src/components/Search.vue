<script setup>
import { onUpdated } from 'vue';
import SearchIcon from './icons/SearchIcon.vue';
import TrackItem from "./TrackItem.vue";

const APIKEY = "239f65d54aeafe4cc8cc31fc73d235e2";

const props = defineProps({
    search: {
        type: String,
        required: true,
        default: ''
    }
})

let tracks = [];

async function searching(event) {
    let inputValue = await event.target.value;
    search = await inputValue;
    let response = await fetch(`http://ws.audioscrobbler.com/2.0/?method=track.search&track=${search}&api_key=${APIKEY}&format=json`);
    let result = await response.json();
    tracks = await result.results.trackmatches.track;
}
</script>

<template>
    <article class="flex items-center relative w-full">
        <label for="search" class="absolute right-0">
            <SearchIcon class="text-slate-600 w-5 h-5 mr-4" />
        </label>
        <input :value="search" @change="searching($event)" type="text" id="search" placeholder="Search . . ."
            class="focus:outline focus:outline-teal-500 rounded-full w-full bg-transparent border border-slate-600 h-fit px-8 py-4">


        <article class="tracks" v-show="tracks.length > 0">
            <TrackItem>
                <template #author>
                    Луверанс
                </template>
                <template #trackName>
                    Душа моя
                </template>
            </TrackItem>
        </article>
    </article>
</template>

<style scoped>
.tracks {
    @apply overflow-hidden rounded-lg mt-4 absolute top-full w-full border border-slate-600;
}
</style>

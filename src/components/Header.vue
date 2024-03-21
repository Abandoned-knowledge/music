<script setup>
import LogoIcon from './icons/LogoIcon.vue';
import Search from './Search.vue';
</script>

<template>
    <header class="flex w-[1200px] mx-auto justify-between items-center gap-10 mt-10">
        <a href="/">
            <LogoIcon class="icon" />
        </a>

        <Search search="" />

        <article class="flex gap-5">
            <a href="/login" class="loginBtn">Login</a>
            <a href="/register" class="registerBtn">Register</a>
        </article>
    </header>
</template>

<style scoped>
.icon {
    width: 48px;
    height: 48px;
}

.loginBtn,
.registerBtn {
    @apply px-8 py-4 rounded-full border border-teal-500 text-white transition-all duration-300;
}

.loginBtn {
    @apply hover:bg-teal-500;
}

.registerBtn {
    @apply bg-teal-500 hover:bg-opacity-0;
}
</style>
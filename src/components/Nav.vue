<script setup>
import { ref } from 'vue';

const isNavOpen = ref(false)

const toggleNav = () => {
  isNavOpen.value = !isNavOpen.value      
}

const toggleNav2 = () => {
  if (isNavOpen.value === true ) {
    isNavOpen.value = false
  }        
}
</script>

<template>
  <header class="mx-6 mt-10 pb-6 flex justify-between relative md:mx-[10%] lg:mx-20 lg:my-14 xl:mx-44 xl:max-w-screen-xl 2xl:mx-auto">
    <div>
      <img src="../assets/images/logo.svg" alt="developer working">  
    </div>

    <nav :class="{ 'nav--open': isNavOpen }">
      <ul class="lg:flex lg:items-center">
        <li class="mt-10 mb-8 font-bold lg:m-0" @click="toggleNav2"><a href="#" class="transition hover:text-[color:var(--darkBlue)]">Features</a></li>
        <li class="my-8 font-bold lg:m-0 lg:px-8" @click="toggleNav2"><a href="#" class="transition hover:text-[color:var(--darkBlue)]">Pricing</a></li>
        <li class="my-8 font-bold lg:m-0" @click="toggleNav2"><a href="#" class="block my-8 font-bold lg:m-0 transition hover:text-[color:var(--darkBlue)]">Resources</a></li>
      </ul>

      <ul class="border-t border-[color:var(--grayishViolet)] lg:border-none lg:flex lg:items-center">
        <li class="my-8 font-bold lg:m-0 lg:pr-8" @click="toggleNav2"><a href="#" class="transition hover:text-[color:var(--darkBlue)]">Login</a></li>
        <li @click="toggleNav2"><a href="#" class="bg-[color:var(--cyan)] text-[color:var(--white)] font-bold w-full rounded-full py-2 mx-auto block mb-10 transition hover:bg-[color:var(--cyanLight)] lg:w-max lg:px-6 lg:m-0">Sign Up</a></li>
      </ul>
    </nav>

    <div class="p-3 relative -top-3 -right-3 cursor-pointer lg:hidden" @click="toggleNav">
      <span class="block h-[3px] w-6 bg-[color:var(--grayishViolet)]"></span>
      <span class="block h-[3px] w-6 bg-[color:var(--grayishViolet)] my-1.5"></span>
      <span class="block h-[3px] w-6 bg-[color:var(--grayishViolet)]"></span>
    </div>
  </header>
</template>

<style>
nav {
  @apply bg-[color:var(--darkViolet)] px-6 absolute z-10 w-full left-0 top-14 h-0 rounded-xl invisible opacity-0 lg:visible lg:opacity-100 lg:bg-[color:var(--white)] lg:relative lg:flex lg:justify-between lg:top-3 lg:pl-8 lg:pr-0;
}

nav.nav--open {
  @apply text-[color:var(--white)] h-auto visible opacity-100 lg:text-[color:var(--grayishViolet)] lg:-top-2;
  transition: 350ms ease-out;
}
</style>
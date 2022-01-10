<script setup>
import { ref, provide, watch, onMounted } from 'vue';
import Nav from "./components/Nav.vue";
import Hero from "./components/Hero.vue";
import Features from "./components/Features.vue";
import Cta from "./components/Cta.vue";
import Footer from "./components/Footer.vue";
import Modal from './components/Modal.vue';

const url = ref()
const formInput = ref()
const errorMessage = ref()
const modalVisible = ref(false)
let allLinks = ref([])

const getShortenedLink = async (payload) => {
  try {
    const request = await fetch("https://api.shrtco.de/v2/shorten?url=" + payload)
    if (!request.ok) {
      errorMessage.value = 'Oops! Error Shortening Link. Check if the link is valid and try again.';
      throw Error(errorMessage.value)
    }
    const response = await request.json();
    return { 
      linkCode: response.result.code,
      shortenedLink: response.result.full_short_link, 
      originalLink: response.result.original_link 
    }    
  } catch (error) {
    toggleModal()
  }
}

const displayLink = (data) => {
  const linkExists = allLinks.value.some(item => item.shortenedLink === data.shortenedLink);

  if (!linkExists) allLinks.value.unshift(data)  
  else {
    errorMessage.value = "Oops! You've already shortened this link";
    toggleModal()    
  }
}

const toggleModal = () => {
  modalVisible.value = !modalVisible.value;
}

const addErrorClass = () => {
  formInput.value.classList.add('focus')
  setTimeout(() => {
    formInput.value.classList.remove('focus')
    formInput.value.focus();
  }, 2000);
}

const handleSubmit = () => {
  if (url.value) {
    getShortenedLink(url.value)
      .then(data => {
        displayLink(data)
      })
      .catch(error => console.log(error.message))
  } else {
    addErrorClass()    
  }
}

watch(allLinks, (current) => {
  localStorage.links = JSON.stringify(current);
}, { deep: true })

onMounted(() => {
  if (localStorage.links) {
    allLinks.value = JSON.parse(localStorage.links)
  }
})

provide('linksArray', allLinks)
</script>

<template>
  <Nav/>
  <Hero/>
  <section class="px-6 py-16 md:px-20 xl:px-0 xl:mx-40 xl:max-w-screen-xl 2xl:mx-auto">
    <form class="p-6 border rounded-xl relative z-10 md:flex md:py-8 md:px-10 lg:text-lg xl:py-12 xl:px-16" @submit.prevent="handleSubmit">
      <div class="mb-4 md:mb-0 md:mr-10 md:flex-grow">
        <input ref="formInput" type="text" placeholder="Shorten a link here..." class="p-3 w-full block rounded-lg lg:py-5 lg:px-8 relative" v-model="url">
      </div>
      
      <button type="submit" class="bg-[color:var(--cyan)] text-[color:var(--white)] w-full p-3 font-bold rounded-lg transition relative z-10 overflow-hidden hover:bg-[color:var(--white)] hover:after:absolute hover:after:top-0 hover:after:left-0 hover:after:h-full hover:after:w-full hover:after:bg-[color:var(--cyanLight)] hover:after:z-[-1]  md:w-max lg:p-5">Shorten It!</button>
    </form>
  </section>
  <Features/>
  <Cta/>
  <Footer/>
  <Modal v-if="modalVisible" @closeEvent="toggleModal" :message="errorMessage"/>
</template>

<style>
form {
  background-image: url('./assets/images/bg-shorten-mobile.svg');
  @apply bg-right-top bg-no-repeat bg-[color:var(--darkViolet)];
}

.focus {
  @apply outline-none;
  outline: 2px solid var(--red);
}

.focus::placeholder {
  @apply text-[color:var(--red)];
}

@media (min-width: 768px) {
  form {
    background-image: url('./assets/images/bg-shorten-desktop.svg');
    @apply bg-center;
  }
}
</style>
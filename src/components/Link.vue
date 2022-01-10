<script setup>
import { ref } from 'vue';

const props = defineProps({ linkInfo: Object });
const buttonClicked = ref(false);
const button = ref();

const copyText = () => {
  navigator.clipboard.writeText(props.linkInfo.shortenedLink);
	buttonClicked.value = true;

	setTimeout(() => {
    buttonClicked.value = false;
  }, 1000);
}
</script>

<template>
  <li class="bg-white rounded-lg text-left mb-6 md:mx-[3.5rem] lg:py-0 xl:mx-20 lg:text-xl lg:flex lg:justify-between lg:items-center  xl:max-w-screen-xl 2xl:mx-auto">
    <p class="border-b border-[color:var(--gray)] px-4 py-3 text-[color:var(--darkBlue)] lg:border-none lg:pl-6">{{ props.linkInfo.originalLink }}</p>
    <div class="lg:flex lg:justify-between lg:items-center">
      <p class="px-4 py-3 text-[color:var(--cyan)] lg:py-0">{{ props.linkInfo.shortenedLink }}</p>
      <div class="w-full p-4 pt-0">
        <button ref="button" class="rounded-md text-center py-3 px-4 w-full bg-[color:var(--cyan)] text-[color:var(--white)] transition-colors lg:font-bold lg:text-base lg:w-28 lg:py-2 lg:mt-4 lg:mr-2" :class="{'bg-[color:var(--darkBlue)]': buttonClicked }" @click='copyText'>
          <span v-if="!buttonClicked">Copy</span>
          <span v-else>Copied!</span>
        </button>
      </div>
    </div>        
  </li>
</template>
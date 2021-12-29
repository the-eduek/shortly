<script setup>
import { inject } from 'vue';
import Link from "./Link.vue";

const linksArray = inject('linksArray');
</script>

<template>
  <section class="bg-[#eef0f6] px-6 pb-0.5 pt-44 -mt-36 md:mt-[-7.5rem] md:pb-14 xl:-mt-36 xl:pb-44 xl:px-[6%] 2xl:px-[10%]">
		<ul class="-mt-20 mb-20">
			<Link v-for="link in linksArray" :key="link.code" :linkInfo="link"/>
		</ul>

		<div class="">
			<h2 class="text-[color:var(--darkBlue)] font-bold text-[1.75rem] tracking-tighter lg:text-[2.5rem]">Advanced Statistics</h2>

			<p class="leading-7 pt-2 pb-4 max-w-xl m-auto md:pb-14 lg:text-xl lg:leading-8">Track how your links are performing across the web with our advanced statistics dashboard.</p>
		</div>

		<div class="relative after:absolute after:w-2 after:h-2/3 after:left-1/2 after:-translate-x-1/2 after:top-[20%] after:bg-[color:var(--cyan)] md:flex md:flex-col md:items-center md:text-left xl:flex-row xl:justify-between xl:after:h-2 xl:after:w-2/3 xl:after:top-[58%] xl:max-w-screen-xl 2xl:mx-auto">
			<div class="bg-[color:var(--white)] px-8 pb-10 pt-0 my-20 rounded-lg relative z-10 md:w-2/3 md:my-10 xl:w-[360px]">
				<div class="bg-[color:var(--darkViolet)] p-6 rounded-full h-[5.5rem] w-[5.5rem] mx-auto relative -top-12 xl:mx-0">
					<img src="../assets/images/icon-brand-recognition.svg">
				</div>
				<h3 class="text-[color:var(--darkBlue)] font-bold text-xl pb-4 -mt-3">Brand Recognition</h3>
				<p class="tracking-tight">Boost your brand recognition with each click. Generic links don’t mean a thing. Branded links help instil confidence in your content.</p>
			</div>

			<div class="bg-[color:var(--white)] px-8 pb-10 pt-0 my-[6.5rem] rounded-lg relative z-10 md:w-2/3 md:my-10 xl:w-[360px] xl:top-12">
				<div class="bg-[color:var(--darkViolet)] p-6 rounded-full h-[5.5rem] w-[5.5rem] mx-auto relative -top-12 xl:mx-0">
					<img src="../assets/images/icon-detailed-records.svg">
				</div>      
				<h3 class="text-[color:var(--darkBlue)] font-bold text-xl pb-4 -mt-3">Detailed Records</h3>
				<p class="tracking-tight">Gain insights into who is clicking your links. Knowing when and where people engage with your content helps inform better decisions.</p>
			</div>

			<div class="bg-[color:var(--white)] px-8 pb-10 pt-0 my-20 rounded-lg relative z-10 md:w-2/3 md:my-10 xl:w-[360px] xl:top-24">
				<div class="bg-[color:var(--darkViolet)] p-6 rounded-full h-[5.5rem] w-[5.5rem] mx-auto relative -top-12 xl:mx-0">
					<img src="../assets/images/icon-fully-customizable.svg">
				</div>					
				<h3 class="text-[color:var(--darkBlue)] font-bold text-xl pb-4 -mt-3">Fully Customizable</h3>
				<p class="tracking-tight">Improve brand awareness and content discoverability through customizable links, supercharging audience engagement.</p>
			</div>
		</div>
	</section>  
</template>


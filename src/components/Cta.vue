<template>
  <section class="text-[color:var(--white)] py-20 md:py-10">
    <h1 class="text-[color:var(--white)] font-bold text-[1.75rem] tracking-tighter py-4 md:text-[42px]">Boost your links today</h1>

    <a href="#form" class="px-10 py-3.5 mx-auto font-bold w-max rounded-full block text-xl bg-[color:var(--cyan)] transition relative z-10 overflow-hidden hover:bg-[color:var(--white)] hover:after:absolute hover:after:top-0 hover:after:left-0 hover:after:h-full hover:after:w-full hover:after:bg-[color:var(--cyanLight)] hover:after:z-[-1] md:mt-1 md:mb-3 md:text-xl">Get Started</a>
  </section>    
</template>

<style scoped>
section {
  background-image: url(../assets/images/bg-boost-mobile.svg);
  background-position: center center;
  background-size: cover;
  background-color: var(--darkViolet);
}

@media (min-width: 768px) {
  section {
    background-image: url(../assets/images/bg-boost-desktop.svg);
  }
}
</style>
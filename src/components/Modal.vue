<script setup>
const emits = defineEmits(['closeEvent'])
const props = defineProps({ message: String })

const toggleModal = () => {
  emits("closeEvent")
}
</script>

<template>
  <section class="fixed top-0 left-0 bg-[#333333cb] z-30 w-full h-full flex items-center justify-center text-[color:var(--darkBlue)] transition" @click.self="toggleModal">
    <div class="bg-[color:var(--white)] w-3/4 rounded-lg">
    <h3 class="text-2xl font-bold py-6 border-b border-[color:var(--gray)]">Error!</h3>
    <p class="px-6 py-4">{{ props.message }}</p>
    </div>
  </section>
</template>
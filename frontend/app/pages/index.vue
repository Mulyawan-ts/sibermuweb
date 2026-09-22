<template>
  <div class="p-8 flex flex-wrap gap-4 items-center bg-base-200 min-h-screen">
    <!-- Primary Button Normal -->
    <AppButton variant="primary"> Simpan Data </AppButton>

    <!-- Secondary Button dengan Ikon -->
    <AppButton variant="secondary" icon="lucide:arrow-left">
      Kembali
    </AppButton>

    <!-- Primary Button dengan Status Loading -->
    <AppButton
      variant="primary"
      icon="lucide:send"
      :loading="isSubmitting"
      @click="handleSubmit"
    >
      Kirim Pesan
    </AppButton>

    <!-- Secondary Button Ukuran Kecil (sm) -->
    <AppButton variant="secondary" size="sm"> Batal </AppButton>
  </div>
</template>

<script setup>
import { ref } from "vue";

const isSubmitting = ref(false);

const handleSubmit = () => {
  isSubmitting.value = true;
  setTimeout(() => {
    isSubmitting.value = false;
  }, 2000);
};
</script>

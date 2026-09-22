<!-- components/AppButton.vue -->
<template>
  <button
    :type="type"
    :disabled="disabled || loading"
    class="btn transition-all duration-200"
    :class="[
      // Murni memetakan varian ke DaisyUI
      variant === 'primary' ? 'btn-primary' : 'btn-secondary',
      // Ukuran opsional: 'xs', 'sm', 'lg'
      size ? `btn-${size}` : '',
      // Status disabled
      { 'btn-disabled': disabled || loading }
    ]"
  >
    <!-- Spinner bawaan DaisyUI saat loading -->
    <span v-if="loading" class="loading loading-spinner loading-sm"></span>

    <!-- Nuxt Icon di sebelah kiri teks (opsional) -->
    <Icon v-if="icon && !loading" :name="icon" class="text-lg" />

    <!-- Teks tombol / konten slot -->
    <slot />
  </button>
</template>

<script setup>
defineProps({
  // Terkunci hanya untuk 'primary' atau 'secondary'
  variant: {
    type: String,
    default: 'primary',
    validator: (val) => ['primary', 'secondary'].includes(val)
  },
  // Ukuran opsional: 'xs', 'sm', 'md', 'lg'
  size: {
    type: String,
    default: ''
  },
  // Nama ikon dari @nuxt/icon (misal: 'lucide:send' atau 'lucide:arrow-left')
  icon: {
    type: String,
    default: ''
  },
  type: {
    type: String,
    default: 'button'
  },
  loading: {
    type: Boolean,
    default: false
  },
  disabled: {
    type: Boolean,
    default: false
  }
})
</script>

<template>
    <div class="min-h-screen bg-gray-100">
      <RegisterForm />
    </div>
  </template>

  <script>
  import RegisterForm from '@/components/RegisterForm.vue'

  export default {
    name: 'App',
    components: {
      RegisterForm
    }
  }
  </script>

<template>
  <header class="bg-white shadow-md">
    <div class="container mx-auto px-4 py-3 flex justify-between items-center">
      <div class="flex items-center space-x-2">
        <div class="w-8 h-8 bg-blue-600 rounded-md"></div>
        <span class="text-xl font-bold text-gray-800">Gestor de Empleados</span>
      </div>
      
      <div class="flex items-center space-x-4">
        <span class="text-gray-600">{{ currentUser }}</span>
        <button 
          @click="handleLogout"
          class="px-4 py-2 text-sm bg-red-100 text-red-700 rounded-md hover:bg-red-200"
        >
          Cerrar Sesión
        </button>
      </div>
    </div>
  </header>
</template>

<script setup>
import { ref, onMounted } from 'vue'
import { useRouter } from 'vue-router'

const router = useRouter()
const currentUser = ref('')

onMounted(() => {
  currentUser.value = localStorage.getItem('currentUser') || 'Usuario'
})

const handleLogout = () => {
  localStorage.removeItem('isAuthenticated')
  localStorage.removeItem('currentUser')
  router.push('/login')
}
</script>
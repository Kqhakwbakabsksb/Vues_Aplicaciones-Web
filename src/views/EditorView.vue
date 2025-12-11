<template>
  <div class="min-h-screen bg-gray-100">
    <HeaderComp />
    
    <div class="flex">
      <aside class="w-64 bg-white shadow-md min-h-[calc(100vh-64px)] p-4">
        <nav class="space-y-2">
          <router-link to="/dashboard" class="block p-2 rounded hover:bg-blue-50">Home</router-link>
          <router-link to="/empleados" class="block p-2 rounded hover:bg-blue-50">Empleados</router-link>
          <router-link to="/reportes" class="block p-2 rounded hover:bg-blue-50">Reportes</router-link>
        </nav>
      </aside>
      
      <main class="flex-1 p-6">
        <div class="flex items-center justify-between mb-6">
          <h1 class="text-3xl font-bold text-gray-800">Editor</h1>
          <router-link 
            to="/empleados"
            class="px-4 py-2 text-gray-600 hover:text-gray-800"
          >
            ← Volver
          </router-link>
        </div>
        
        <div class="bg-white rounded-lg shadow-md p-6 max-w-2xl">
          <h2 class="text-xl font-semibold text-gray-700 mb-6 pb-4 border-b">Empleado</h2>
          
          <form @submit.prevent="guardarEmpleado" class="space-y-6">
            <div class="grid grid-cols-1 md:grid-cols-2 gap-6">
              <div>
                <label class="block text-sm font-medium text-gray-700 mb-1">Nombre</label>
                <input
                  v-model="empleado.nombre"
                  type="text"
                  placeholder="Nombre completo"
                  class="w-full px-3 py-2 border border-gray-300 rounded-md focus:outline-none focus:ring-2 focus:ring-blue-500"
                  required
                />
              </div>
              
              <div>
                <label class="block text-sm font-medium text-gray-700 mb-1">ID</label>
                <input
                  v-model="empleado.id"
                  type="text"
                  placeholder="ID del empleado"
                  class="w-full px-3 py-2 border border-gray-300 rounded-md focus:outline-none focus:ring-2 focus:ring-blue-500"
                  required
                />
              </div>
              
              <div>
                <label class="block text-sm font-medium text-gray-700 mb-1">Correo</label>
                <input
                  v-model="empleado.correo"
                  type="email"
                  placeholder="correo@empresa.com"
                  class="w-full px-3 py-2 border border-gray-300 rounded-md focus:outline-none focus:ring-2 focus:ring-blue-500"
                  required
                />
              </div>
              
              <div>
                <label class="block text-sm font-medium text-gray-700 mb-1">Credencial</label>
                <input
                  v-model="empleado.credencial"
                  type="text"
                  placeholder="Número de credencial"
                  class="w-full px-3 py-2 border border-gray-300 rounded-md focus:outline-none focus:ring-2 focus:ring-blue-500"
                  required
                />
              </div>
            </div>
            
            <div>
              <label class="block text-sm font-medium text-gray-700 mb-1">Departamento</label>
              <select
                v-model="empleado.departamento"
                class="w-full px-3 py-2 border border-gray-300 rounded-md focus:outline-none focus:ring-2 focus:ring-blue-500"
              >
                <option value="">Seleccionar departamento</option>
                <option value="Ventas">Ventas</option>
                <option value="Marketing">Marketing</option>
                <option value="Recursos Humanos">Recursos Humanos</option>
                <option value="Ingenieria">Ingenieria</option>
                <option value="Finanzas">Finanzas</option>
              </select>
            </div>
            
            <div>
              <label class="block text-sm font-medium text-gray-700 mb-1">Salario Anual</label>
              <input
                v-model="empleado.salario"
                type="number"
                placeholder="0.00"
                class="w-full px-3 py-2 border border-gray-300 rounded-md focus:outline-none focus:ring-2 focus:ring-blue-500"
              />
            </div>
            
            <div class="flex justify-end space-x-4 pt-4 border-t">
              <button
                type="button"
                @click="eliminarEmpleado"
                class="px-6 py-2 bg-red-100 text-red-700 rounded-md hover:bg-red-200"
                v-if="empleadoEditando"
              >
                Eliminar
              </button>
              <button
                type="submit"
                class="px-6 py-2 bg-blue-600 text-white rounded-md hover:bg-blue-700"
              >
                Guardar
              </button>
            </div>
          </form>
        </div>
      </main>
    </div>
  </div>
</template>

<script setup>
import { ref, onMounted } from 'vue'
import { useRoute, useRouter } from 'vue-router'
import HeaderComp from '@/components/HeaderComp.vue'

const route = useRoute()
const router = useRouter()

const empleadoEditando = ref(false)

const empleado = ref({
  nombre: '',
  id: '',
  correo: '',
  credencial: '',
  departamento: '',
  salario: ''
})

onMounted(() => {
  // Se edita con ID
  if (route.params.id) {
    empleadoEditando.value = true
    // Aquí se cargan los datos del empleado desde una API
    cargarEmpleado(route.params.id)
  }
})

const cargarEmpleado = (id) => {
  // Simulación de carga de datos
  empleado.value = {
    nombre: 'Roberto Castro',
    id: id,
    correo: 'roberto1@gmail.com',
    credencial: 'EMP-001',
    departamento: 'Recursos Humanos',
    salario: '288000'
  }
}

const guardarEmpleado = () => {
  alert(empleadoEditando.value ? 'Empleado actualizado' : 'Empleado creado')
  router.push('/empleados')
}

const eliminarEmpleado = () => {
  if (confirm('¿Está seguro de eliminar este empleado?')) {
    alert('Empleado eliminado')
    router.push('/empleados')
  }
}
</script>
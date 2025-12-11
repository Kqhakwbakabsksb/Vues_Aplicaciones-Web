<template>
  <div class="min-h-screen bg-gray-100">
    <HeaderComp />
    
    <div class="flex">
      <!-- Sidebar -->
      <aside class="w-64 bg-white shadow-md min-h-[calc(100vh-64px)] p-4">
        <nav class="space-y-2">
          <router-link 
            to="/dashboard" 
            class="block p-2 rounded hover:bg-blue-50 text-blue-600 font-medium"
            :class="{ 'bg-blue-100': $route.path === '/dashboard' }"
          >
            Home
          </router-link>
          <router-link 
            to="/empleados" 
            class="block p-2 rounded hover:bg-blue-50"
            :class="{ 'bg-blue-100': $route.path === '/empleados' }"
          >
            Empleados
          </router-link>
          <router-link 
            to="/reportes" 
            class="block p-2 rounded hover:bg-blue-50"
            :class="{ 'bg-blue-100': $route.path === '/reportes' }"
          >
            Reportes
          </router-link>
        </nav>
      </aside>
      
      <!-- Contenido relevante Armando y gabs -->
      <main class="flex-1 p-6">
        <h1 class="text-3xl font-bold text-gray-800 mb-6">Gestor de Empleados</h1>
        
        <div class="bg-white rounded-lg shadow-md p-6 mb-6">
          <h2 class="text-xl font-semibold text-gray-700 mb-4">Departamentos</h2>
          
          <nav class="flex space-x-4 mb-4">
            <router-link 
              to="/empleados" 
              class="px-4 py-2 bg-blue-100 text-blue-700 rounded-md hover:bg-blue-200"
            >
              Empleados
            </router-link>
            <router-link 
              to="/reportes" 
              class="px-4 py-2 bg-green-100 text-green-700 rounded-md hover:bg-green-200"
            >
              Reportes
            </router-link>
          </nav>
        </div>
        
        <div class="bg-white rounded-lg shadow-md p-6">
          <h2 class="text-xl font-semibold text-gray-700 mb-4">Departamentos</h2>
          
          <DepartamentoTable :departamentos="departamentos" />
        </div>
      </main>
    </div>
  </div>
</template>

<script setup>
import { ref } from 'vue'
import HeaderComp from '@/components/HeaderComp.vue'
import DepartamentoTable from '@/components/DepartamentoTable.vue'

const departamentos = ref([
  { nombre: 'Ventas', gerente: 'Jesus Armando', correo: 'Armando1@gmail.com', empleados: 12 },
  { nombre: 'Marketing', gerente: 'Evelyn Guzman', correo: 'Evelyn2@gmail.com', empleados: 8 },
  { nombre: 'Recursos Humanos', gerente: 'Roberto Castro', correo: 'Roberto3@gmail.com', empleados: 5 },
  { nombre: 'Ingenieria', gerente: 'Luis Fernando', correo: 'Fernando4@gmail.com', empleados: 15 },
  { nombre: 'Finanzas', gerente: 'Dainiz', correo: 'Dainiz5@gmail.com', empleados: 9 }
])
</script>
<template>
  <div class="min-h-screen bg-gray-100">
    <HeaderComp />
    
    <div class="flex">
      <aside class="w-64 bg-white shadow-md min-h-[calc(100vh-64px)] p-4">
        <nav class="space-y-2">
          <router-link to="/dashboard" class="block p-2 rounded hover:bg-blue-50">Home</router-link>
          <router-link to="/empleados" class="block p-2 rounded hover:bg-blue-50">Empleados</router-link>
          <router-link to="/reportes" class="block p-2 rounded bg-blue-100 text-blue-600 font-medium">Reportes</router-link>
        </nav>
      </aside>
      
      <main class="flex-1 p-6">
        <h1 class="text-3xl font-bold text-gray-800 mb-6">Reportes</h1>
        
        <div class="grid grid-cols-1 md:grid-cols-3 gap-6 mb-8">
          <div class="bg-white rounded-lg shadow-md p-6">
            <h3 class="text-lg font-semibold text-gray-700 mb-2">Total Empleados</h3>
            <p class="text-3xl font-bold text-blue-600">49</p>
          </div>
          
          <div class="bg-white rounded-lg shadow-md p-6">
            <h3 class="text-lg font-semibold text-gray-700 mb-2">Salario Promedio</h3>
            <p class="text-3xl font-bold text-green-600">$215,000</p>
          </div>
          
          <div class="bg-white rounded-lg shadow-md p-6">
            <h3 class="text-lg font-semibold text-gray-700 mb-2">Departamentos</h3>
            <p class="text-3xl font-bold text-purple-600">5</p>
          </div>
        </div>
        
        <div class="bg-white rounded-lg shadow-md p-6">
          <h2 class="text-xl font-semibold text-gray-700 mb-4">Distribución por Departamento</h2>
          
          <div class="space-y-4">
            <div v-for="dept in departamentos" :key="dept.nombre" class="border-b pb-4 last:border-0">
              <div class="flex justify-between mb-1">
                <span class="font-medium">{{ dept.nombre }}</span>
                <span>{{ dept.empleados }} empleados</span>
              </div>
              <div class="w-full bg-gray-200 rounded-full h-2">
                <div 
                  :class="dept.color" 
                  :style="{ width: `${(dept.empleados / 49) * 100}%` }"
                  class="h-2 rounded-full"
                ></div>
              </div>
            </div>
          </div>
        </div>
      </main>
    </div>
  </div>
</template>

<script setup>
import { ref } from 'vue'
import HeaderComp from '@/components/HeaderComp.vue'

const departamentos = ref([
  { nombre: 'Ventas', empleados: 12, color: 'bg-blue-500' },
  { nombre: 'Marketing', empleados: 8, color: 'bg-green-500' },
  { nombre: 'Recursos Humanos', empleados: 5, color: 'bg-yellow-500' },
  { nombre: 'Ingenieria', empleados: 15, color: 'bg-red-500' },
  { nombre: 'Finanzas', empleados: 9, color: 'bg-purple-500' }
])
</script>
<template>
  <div class="min-h-screen bg-gray-100">
    <HeaderComp />
    
    <div class="flex">
      <aside class="w-64 bg-white shadow-md min-h-[calc(100vh-64px)] p-4">
        <nav class="space-y-2">
          <router-link to="/dashboard" class="block p-2 rounded hover:bg-blue-50">Home</router-link>
          <router-link to="/empleados" class="block p-2 rounded bg-blue-100 text-blue-600 font-medium">Empleados</router-link>
          <router-link to="/reportes" class="block p-2 rounded hover:bg-blue-50">Reportes</router-link>
        </nav>
      </aside>
      
      <main class="flex-1 p-6">
        <h1 class="text-3xl font-bold text-gray-800 mb-6">Empleados</h1>
        
        <div class="bg-white rounded-lg shadow-md p-6 mb-6">
          <div class="border-b pb-4 mb-4">
            <h2 class="text-2xl font-semibold text-gray-800">Roberto Castro</h2>
            <p class="text-gray-600">roberto1@gmail.com</p>
          </div>
          
          <table class="min-w-full">
            <thead class="bg-gray-50">
              <tr>
                <th class="px-4 py-3 text-left text-sm font-medium text-gray-700">Departamento</th>
                <th class="px-4 py-3 text-left text-sm font-medium text-gray-700">Fecha de registro</th>
                <th class="px-4 py-3 text-left text-sm font-medium text-gray-700">Salario Anual</th>
              </tr>
            </thead>
            <tbody>
              <tr class="border-b hover:bg-gray-50">
                <td class="px-4 py-3">Recursos Humanos</td>
                <td class="px-4 py-3">Octubre 09, 2025</td>
                <td class="px-4 py-3 font-medium">$288,000</td>
              </tr>
            </tbody>
          </table>
        </div>
        
        <div class="flex justify-end space-x-4">
          <router-link 
            to="/editor"
            class="px-4 py-2 bg-blue-600 text-white rounded-md hover:bg-blue-700"
          >
            Agregar Empleado
          </router-link>
          <button class="px-4 py-2 bg-gray-200 text-gray-800 rounded-md hover:bg-gray-300">
            Exportar
          </button>
        </div>
      </main>
    </div>
  </div>
</template>

<script setup>
import HeaderComp from '@/components/HeaderComp.vue'
</script>
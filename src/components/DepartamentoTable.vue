<template>
  <div class="overflow-x-auto">
    <table class="min-w-full divide-y divide-gray-200">
      <thead class="bg-gray-50">
        <tr>
          <th class="px-6 py-3 text-left text-xs font-medium text-gray-500 uppercase tracking-wider">
            Nombre
          </th>
          <th class="px-6 py-3 text-left text-xs font-medium text-gray-500 uppercase tracking-wider">
            Gerente
          </th>
          <th class="px-6 py-3 text-left text-xs font-medium text-gray-500 uppercase tracking-wider">
            Correo
          </th>
          <th class="px-6 py-3 text-left text-xs font-medium text-gray-500 uppercase tracking-wider">
            No. Empleados
          </th>
          <th class="px-6 py-3 text-left text-xs font-medium text-gray-500 uppercase tracking-wider">
            Acciones
          </th>
        </tr>
      </thead>
      <tbody class="bg-white divide-y divide-gray-200">
        <tr v-for="dept in departamentos" :key="dept.nombre">
          <td class="px-6 py-4 whitespace-nowrap font-medium text-gray-900">
            {{ dept.nombre }}
          </td>
          <td class="px-6 py-4 whitespace-nowrap text-gray-700">
            {{ dept.gerente }}
          </td>
          <td class="px-6 py-4 whitespace-nowrap text-gray-700">
            {{ dept.correo }}
          </td>
          <td class="px-6 py-4 whitespace-nowrap text-gray-700">
            {{ dept.empleados }}
          </td>
          <td class="px-6 py-4 whitespace-nowrap text-sm">
            <button 
              @click="$emit('editar', dept)"
              class="mr-2 px-3 py-1 bg-blue-100 text-blue-700 rounded-md hover:bg-blue-200"
            >
              Editar
            </button>
            <button 
              @click="confirmarEliminar(dept)"
              class="px-3 py-1 bg-red-100 text-red-700 rounded-md hover:bg-red-200"
            >
              Eliminar
            </button>
          </td>
        </tr>
      </tbody>
    </table>
  </div>
</template>

<script setup>
defineProps({
  departamentos: {
    type: Array,
    required: true
  }
})

const emit = defineEmits(['editar', 'eliminar'])

const confirmarEliminar = (dept) => {
  if (confirm(`¿Está seguro de eliminar el departamento "${dept.nombre}"?`)) {
    emit('eliminar', dept)
  }
}
</script>
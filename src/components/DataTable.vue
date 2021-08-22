<template>
  <!-- Data Table display -->
  <div class="w-full sm:px-6">
    <div
      class="bg-white shadow px-4 md:px-10 pt-4 md:pt-7 pb-5 overflow-y-auto"
    >
      <table class="w-full whitespace-nowrap">
        <thead>
          <tr
            tabindex="0"
            class="
              focus:outline-none
              h-16
              w-full
              text-sm
              leading-none
              text-gray-800
            "
          >
            <th class="text-2xl text-black-900 text-left font-bold mb-4">Position</th>
            <th class="text-2xl text-black-900 text-left font-bold mb-12">Driver</th>
            <th class="text-2xl text-black-900 text-left font-bold mb-12">Num</th>
            <th class="text-2xl text-black-900 text-left font-bold mb-16">Nationality</th>
            <th class="text-2xl text-black-900 text-left font-bold mb-16">Points</th>
            <th class="text-2xl text-black-900 text-left font-bold mb-20">Wins</th>
          </tr>
        </thead>
        <tbody class="w-full">
          <tr
            tabindex="0"
            class="
              focus:outline-none
              h-20
              text-lg
              leading-none
              text-green-800
              bg-white
              hover:bg-gray-100
              border-b border-t border-gray-100
            "
            v-for="driver in drivers"
            :key="driver"
          >
            <td class="pl-4 cursor-pointer">
              <div class="flex items-center">
                <div class="w-10 h-10">
                  <!-- <img class="w-full h-full" src="../assets/f1logo.png" /> -->
                  <i class="fas fa-trophy fa-3x"></i>
                </div>
                <div class="pl-12">
                  <p class="font-medium">{{ driver.position }}</p>
                </div>
              </div>
            </td>
            <td class="pl-4">
              <p class="font-medium">
                {{ driver.Driver.code }}
              </p>
            </td>
            <td class="pl-4">
              <p class="font-medium">{{ driver.Driver.permanentNumber }}</p>
            </td>
            <td class="pl-4">
              <p class="font-medium">{{ driver.Driver.nationality }}</p>
            </td>
            <td class="pl-4">
              <p class="font-medium">{{ driver.points }}</p>
            </td>
            <td class="pl-4">
              <p class="font-medium">{{ driver.wins }}</p>
            </td>
          </tr>
        </tbody>
      </table>
    </div>
  </div>
</template>

<script>
export default {
  name: "DataTable",
  props: ["drivers"],
};
</script>

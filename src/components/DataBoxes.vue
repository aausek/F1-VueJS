<template>
  <!-- <div
    class="grid md:grid-cols-2 gap-5"
    v-for="driver in drivers"
    :key="driver"> -->
  <!-- Box 1 -->
  <!-- <div class="shadow-md bg-gray-200 p-10 text-center rounded">
      <h3 class="text-3xl text-blue-900 font-bold mb-4">Driver Info</h3>

      <div class="text-2xl mb-4">
        <span class="font-bold">Driver:</span>
        {{ driver.Driver.code }}
      </div>

      <div class="text-2xl mb-4">
        <span class="font-bold">Racing Number:</span>
        {{ driver.Driver.permanentNumber }}
      </div>

      <div class="text-2xl mb-4">
        <span class="font-bold">Nationality:</span>
        {{ driver.Driver.nationality }}
      </div>
    </div> -->

  <!-- Box 2 -->
  <!-- <div class="shadow-md bg-gray-200 p-10 text-center rounded">
      <h3 class="text-3xl text-blue-900 font-bold mb-4">Driver Stats</h3>

      <div class="text-2xl mb-4">
        <span class="font-bold">Position:</span>
        {{ driver.position }}
      </div>

      <div class="text-2xl mb-4">
        <span class="font-bold">Points:</span>
        {{ driver.points }}
      </div>

      <div class="text-2xl mb-4">
        <span class="font-bold">Wins:</span>
        {{ driver.wins }}
      </div>
    </div>
  </div> -->

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
            <th class="text-2xl text-black-900 font-bold mb-4">Position</th>
            <th class="text-2xl text-black-900 font-bold mb-4">Driver</th>
            <th class="text-2xl text-black-900 font-bold mb-4">Num</th>
            <th class="text-2xl text-black-900 font-bold mb-4">Nationality</th>
            <th class="text-2xl text-black-900 font-bold mb-4">Points</th>
            <th class="text-2xl text-black-900 font-bold mb-4">Wins</th>
          </tr>
        </thead>
        <tbody class="w-full">
          <tr
            tabindex="0"
            class="
              focus:outline-none
              h-20
              text-sm
              leading-none
              text-gray-800
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
                  <img class="w-full h-full" src="../assets/f1logo.png" />
                </div>
                <div class="pl-4">
                  <p class="font-medium">{{ driver.position }}</p>
                </div>
              </div>
            </td>
            <td class="pl-12">
              <p class="text-sm font-medium leading-none text-gray-800">
                {{ driver.Driver.code }}
              </p>
            </td>
            <td class="pl-12">
              <p class="font-medium">{{ driver.Driver.permanentNumber }}</p>
            </td>
            <td class="pl-20">
              <p class="font-medium">{{ driver.Driver.nationality }}</p>
            </td>
            <td class="pl-20">
              <p class="font-medium">{{ driver.points }}</p>
            </td>
            <td class="pl-20">
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
  name: "DataBoxes",
  props: [
    "season",
    "drivers",
    "racingNum",
    "nationality",
    "position",
    "points",
    "wins",
  ],
};
</script>

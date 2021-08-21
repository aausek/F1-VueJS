<template>
  <div
    class="grid md:grid-cols-2 gap-5"
    v-for="driver in drivers"
    :key="driver">
    <!-- Box 1 -->
    <div class="shadow-md bg-gray-200 p-10 text-center rounded">
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
    </div>

    <!-- Box 2 -->
    <div class="shadow-md bg-gray-200 p-10 text-center rounded">
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

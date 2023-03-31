<template>
  <div class="grid md:grid-cols-2 gap-4" >
    <!-- Box 1 -->
    <div class="shadow-md bg-blue-100 p-10 text-center rounded">
      <h3 class="text-3xl text-blue-900 font-bold mb-4">Drivers</h3>

      <div class="text-2xl mb-4">
        <span class="font-bold">Position:</span>
        {{  }}
      </div>
      <div class="text-2xl mb-4">
        <span class="font-bold">Wins:</span>
        {{  }}
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: 'DataBoxes',
  props: ['drivers']
};
</script>
<template>
  <select
    v-model="selected"
    class="form-select mt-4 mb-10 block w-full border p-3 rounded"
    @change="onChange"
  >
    <option value="0">Select Driver</option>
    <option v-for="driver in stats" v-bind:value="driver.Driver.code">
      {{ driver.Driver.code }}
    </option>
  </select>
</template>

<script>
import { ref } from 'vue';

export default {
  name: 'FilterSelect',
  props: ['stats'],
  setup ({ stats }, { emit }) {
    const selected = ref(0);

    return {
      selected,
      onChange () {
        const driver = stats.find((item) => item.Driver.code === selected.value);
        emit('get-driver', driver);
        console.log(driver);
      },
      
    };
  }
};
</script>
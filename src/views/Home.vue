<template>
  <main v-if="!loading">
    <SeasonTitle :season="season" />

    <FilterSelect :drivers="drivers" @get-driver="getDriver" />

    <DataTable :drivers="drivers" />
  </main>

  <main class="flex flex-col align-center justify-center text-center" v-else>
    <div class="text-3xl md:text-5xl mb-10">Fetching Data</div>
    <img :src="loadingImage" class="w-32 m-auto" alt="" />
    <!-- <iframe src="https://giphy.com/embed/F3JhKaucb9QqSF7bSS" 
    frameBorder="0" class="w-100"></iframe> -->
  </main>
</template>

<script>
import SeasonTitle from "@/components/SeasonTitle";
import DataTable from "@/components/DataTable";
import FilterSelect from "@/components/FilterSelect";
import { ref } from 'vue';

export default {
  name: "Home",
  components: {
    SeasonTitle,
    DataTable,
    FilterSelect,
  },
  data() {
    return {
      loading: true,
      drivers: [],
      season: "",
      loadingImage: require("../assets/gif.webp"),
    };
  },
  methods: {
    fetchData() {
      fetch("http://ergast.com/api/f1/2021/driverStandings.json")
        .then((response) => response.json())
        .then((response) => {
          this.drivers =
            response.MRData.StandingsTable.StandingsLists[0].DriverStandings;
          this.season = response.MRData.StandingsTable.StandingsLists[0].season;
          //console.log(response.MRData)
          this.loading = false;
        });
    },
    getDriver(driver) {
      this.drivers.Driver = driver;
      console.log(this.drivers.Driver);
    },
  },
    created() {
      this.fetchData();
      this.loading = true;
    },
};

// ----------------

// export default {
//   name: "Home",
//   components: {
//     SeasonTitle,
//     DataTable,
//     FilterSelect,
//   },
//   setup () {
//     const loading = ref(true);
//     const season = ref('');
//     const drivers = ref([]);
//     const fetchData = async () => {
//       const res = await fetch('http://ergast.com/api/f1/2021/driverStandings.json');
//       //console.log(res);
//       return await res.json();
//     };
    
//     const getDriver = (driver) => {
//       drivers.value = driver;
//       //console.log(driver);
//     };

//     const clearData = async () => {
//       loading.value = true;
//       const data = await fetchData();
//       drivers.value = data.MRData.StandingsTable.StandingsLists[0].DriverStandings;
//       loading.value = false;
//     };

//     const baseSetup = async () => {
//       const data = await fetchData();
//       drivers.value = data.MRData.StandingsTable.StandingsLists[0].DriverStandings;
//       season.value = data.MRData.StandingsTable.StandingsLists[0].season;
//       loading.value = false;
//     };

//     baseSetup();
    
//     return {
//       loading,
//       loadingImage: require("../assets/gif.webp"),
//       drivers,
//       season,
//       getDriver,
//       clearData
//     };
//   }
// };


</script>

<template>
  <main v-if="!loading">
    <Header :season="season" />
    
    <SeasonTitle :season="season" />

    <FilterSelect :stats="stats" @get-driver="getDriverData"/>

    <DataTable :stats="stats" />
    
  </main>

  <main class="flex flex-col align-center justify-center text-center" v-else>
    <div class="text-3xl md:text-5xl mb-10">Fetching Data</div>
    <img :src="loadingImage" class="w-32 m-auto" alt="" />
    <!-- <iframe src="https://giphy.com/embed/F3JhKaucb9QqSF7bSS" 
    frameBorder="0" class="w-100"></iframe> -->
  </main>

      <!-- <v-btn text @click="darkMode">
      <font-awesome-icon
        v-if="$vuetify.theme.dark"
        icon="fa-solid fa-sun"
        size="lg"
      />
      <font-awesome-icon v-else icon="fa-solid fa-moon" size="lg" />
      <span class="ml-2">
        {{ $vuetify.theme.dark ? "Ligh Mode" : "Dark Mode" }}</span
      >
    </v-btn> -->
</template>

<script>
import SeasonTitle from "@/components/SeasonTitle";
import DataTable from "@/components/DataTable";
import DataBoxes from "@/components/DataBoxes";
import FilterSelect from "@/components/FilterSelect";
import Header from "@/components/Header";
import { ref } from 'vue';
import _ from 'lodash';
import DriverStandingsData from "../data/driverstandings2022.json";

// export default {
//   name: "Home",
//   components: {
//     SeasonTitle,
//     DataTable,
//     FilterSelect,
//   },
//   data() {
//     return {
//       loading: true,
//       stats: [],
//       season: "",
//       loadingImage: require("../assets/gif.webp"),
//     };
//   },
//   methods: {
//     fetchData() {
//       fetch("http://ergast.com/api/f1/2021/statstandings.json")
//         .then((response) => response.json())
//         .then((response) => {
//           this.stats =
//             response.MRData.StandingsTable.StandingsLists[0].statstandings;
//           this.season = response.MRData.StandingsTable.StandingsLists[0].season;
//           //console.log(response.MRData)
//           this.loading = false;
//         });
//     },
//     getDriver(driver) {
//       stats.value = driver;
//       // console.log(this.stats.Driver);
//     },
//   },
//     created() {
//       this.fetchData();
//       this.loading = true;
//     },
// };
// ----------------
export default {
  name: "Home",
  components: {
    SeasonTitle,
    DataTable,
    DataBoxes,
    FilterSelect,
    Header,
    DriverStandingsData
  },
  setup () {
    const loading = ref(true);
    const season = ref('');
    const prevSeason = new Date().getFullYear() - 1;
    const stats = ref({});
    const driverCodes = ref([]);

    // const fetchData = async () => {
    //   const res = await fetch('http://ergast.com/api/f1/' + prevSeason + '/driverStandings.json');
    //   //console.log(res);
    //   return await res.json();
    // };
    
    const getDriverData = (driver) => {
      stats.value = DriverStandingsData.driver;
      // driverCodes.value = driver.Driver.code;
      console.log(driver);
    };
    console.log(DriverStandingsData);

    const clearData = async () => {
      loading.value = true;
      // const data = await fetchData();
      const data = DriverStandingsData;
      stats.value = data.MRData.StandingsTable.StandingsLists[0].DriverStandings;
      loading.value = false;
    };

    const baseSetup = async () => {
      // const data = await fetchData();

      const data = DriverStandingsData;

      stats.value = data.MRData.StandingsTable.StandingsLists[0].DriverStandings;
      // Console 
      console.log(stats._rawValue);
      season.value = data.MRData.StandingsTable.StandingsLists[0].season;
      loading.value = false;

      for(var i = 0; i < data.length; i++) {
        var obj = data[i];
        console.log(obj.id);
      };
    };

    // TODO
    const darkMode = async () => {
      this.$vuetify.theme.dark = !this.$vuetify.theme.dark;
    };

    baseSetup();
    
    return {
      loading,
      loadingImage: require("../assets/gif.webp"),
      stats,
      season,
      getDriverData,
      clearData,
      darkMode
    };
  }
};
</script>
<template>
  <main v-if="!loading">
    <SeasonTitle :season="season" />

    <DataTable :drivers="drivers"/>
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

export default {
  name: "Home",
  components: {
    SeasonTitle,
    DataTable
  },
  data() {
    return {
      loading: true,
      drivers: [],
      season: "",
      loadingImage: require("../assets/gif.webp")
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
  },
  created() {
    this.fetchData();
    this.loading = true;
  },
};
</script>

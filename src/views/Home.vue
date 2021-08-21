<template>
  <main v-if="!loading">
    <SeasonTitle :season="season" />

    <DataBoxes
      :drivers="drivers"
      :racingNum="racingNum"
      :nationality="nationality"
      :points="points"
      :wins="wins"
      :position="position"
    />
  </main>

  <main class="flex flex-col align-center justify-center text-center" v-else>
    <div class="text-black-500 text-3xl mt-10 mb-6">Fetching Data</div>
    <img :src="loadingImage" class="w-24 m-auto" alt="" />
  </main>
</template>

<script>
import SeasonTitle from "@/components/SeasonTitle";
import DataBoxes from "@/components/DataBoxes";

export default {
  name: "Home",
  components: {
    SeasonTitle,
    DataBoxes,
  },
  data() {
    return {
      loading: true,
      drivers: [],
      season: "",
      loadingImage: require("../assets/buffering.gif"),
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
        });
    },
  },
  created() {
    this.fetchData();

    this.loading = false;
  },
};
</script>

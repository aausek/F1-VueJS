<template>
  
  <main v-if="!loading">
    <SeasonTitle :season="season" />

    <DataBoxes :drivers="drivers" :racingNum="racingNum" :nationality="nationality" :points="points" :wins="wins" :position="position" />
  </main>

  <main class="flex flex-col align-center justify-center text-center" v-else>
    <div class="text-black-500 text-3xl mt-10 mb-6">
      Fetching Data
    </div>
    <img :src="loadingImage" class="w-24 m-auto" alt="" />
  </main>

</template>

<script>
import SeasonTitle from '@/components/SeasonTitle'
import DataBoxes from '@/components/DataBoxes'

export default {
  name: 'Home',
  components: {
    SeasonTitle,
    DataBoxes
  },
  data() {
    return {
      loading: true,
      drivers: [],
      //title: 'Global',
      season: '',
      // racingNum: '',
      // nationality: '',
      // position: '',
      // points: '',
      // wins: '',
      loadingImage: require('../assets/buffering.gif')
    }
  },
  methods: {
    fetchData(){
      fetch('http://ergast.com/api/f1/2021/driverStandings.json')
      .then(response => response.json())
      // .then(json => this.seasonData = json.MRData.StandingsTable.StandingsLists[0])
      .then(response => {
        this.drivers = response.MRData.StandingsTable.StandingsLists[0].DriverStandings
        this.season = response.MRData.StandingsTable.StandingsLists[0].season
        //console.log(response.MRData)
      })
    }
  },
  created(){
    this.fetchData();
  
    // this.season = this.seasonData.season
    // this.drivers = data.MRData.StandingsTable.StandingsLists[0].DriverStandings[0].Driver.code
    // this.racingNum = data.MRData.StandingsTable.StandingsLists[0].DriverStandings[0].Driver.permanentNumber
    // this.nationality = data.MRData.StandingsTable.StandingsLists[0].DriverStandings[0].Driver.nationality
    // this.position = data.MRData.StandingsTable.StandingsLists[0].DriverStandings[0].position
    // this.points = data.MRData.StandingsTable.StandingsLists[0].DriverStandings[0].points
    // this.wins = data.MRData.StandingsTable.StandingsLists[0].DriverStandings[0].wins
    
    this.loading = false

    // console.log(this.season)
    // console.log(this.drivers)
    // console.log(this.racingNum)
    // console.log(this.nationality)
    // console.log(this.position)
    // console.log(this.points)
    // console.log(this.wins)
  }
}
</script>

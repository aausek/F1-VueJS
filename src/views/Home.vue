<template>
  
  <main v-if="!loading">
    <SeasonTitle :text="title" :season="season" />
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

export default {
  name: 'Home',
  components: {
    SeasonTitle
  },
  data() {
    return {
      loading: true,
      title: 'Global',
      season: '',
      status: {},
      drivers: [],
      season: '',
      loadingImage: require('../assets/buffering.gif')
    }
  },
  methods: {
    async fetchData(){
      const res = await fetch('http://ergast.com/api/f1/2021/driverStandings.json')
      const data = await res.json()
      return data
    }
  },
  async created(){
    const data = await this.fetchData()

    this.season = data.MRData.StandingsTable.season
    this.drivers = data.MRData.StandingsTable.StandingsLists[0].DriverStandings[0].Driver.code
    this.loading = false

    console.log(this.season)
    console.log(this.drivers)
  },
}
</script>

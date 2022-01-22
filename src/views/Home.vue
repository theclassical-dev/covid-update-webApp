<template>
  <main v-if="!loading">
      <DataTitle :text="title" :dataDate="dataDate" />
  </main>
  <main v-else class="flex flex-col align-center justify-center text-center items-center">
      <div class="text-gray-500 text-3xl mt-10 mb-6">Fatching</div>
      <img :src="loadingImage" class="w-24 m-auto">
  </main>
</template>

<script>
import DataTitle from '@/components/DataTitle'

export default {
    name: 'Home',
    components:{
        DataTitle
    },
    data() {
        return {
            loading: true,
            title: 'Global',
            dataDate: '',
            status:{},
            countries: [],
            loadingImage: require('../assets/01.gif'),
        }
    },
    methods: {
        async fetchData() {
            const res = await fetch('https://api.covid19api.com/summary')
            const data = await res.json()
            return data
        },
    },
    async created() {
        const data = await this.fetchData()

        this.dataDate = data.Date
        this.status = data.Global
        this.countries = data.Countries
        this.loading  = false
    }
}
</script>
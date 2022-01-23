<template>
    <main v-if="!loading">
        <DataTitle class="text-white" :text="title" :dataDate="dataDate" />
        <!-- data div -->
        <DataDiv :status="status"/>
        <!-- countries div -->
        <Countries @getCountry="getData" :countries="countries" />
        <!-- button -->
        <button @click="Refresh" v-if="status.Country" class="bg-green-700 text-white rounded p-3 mt-10 mb-5 sm:mb-0 focus:outline-none hover:bg-gray-600">Refresh</button>
        <!-- footer -->
        <Footer />
    </main>
  <main v-else class="flex flex-col align-center justify-center text-center items-center">
      <div class="text-gray-500 text-3xl mt-10 mb-6">Fatching</div>
      <img :src="loadingImage" class="w-24 m-auto">
  </main>
</template>

<script>
import DataTitle from '@/components/DataTitle'
import DataDiv from '@/components/DataDiv'
import Countries from '@/components/Countries'
import Footer from '@/components/Footer'

export default {
    name: 'Home',
    components:{
        DataTitle,
        DataDiv,
        Countries,
        Footer
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
        getData(country) {
            this.status = country
            this.title = country.Country

            this.$emit('update', country)
        },
        async Refresh() {
            this.loading = true
            const data = await this.fetchData()
            this.title = 'Global'
            this.status = data.Global
            this.loading = false
        }
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
<template>
    <!-- <div class="justify-center"> -->
        <select @change="onChange()" v-model="selected" name="" id="" 
        class="form-select mt-10 block w-full border p-3 rounded"
        >
            <option value="0">Select Country</option>
            <option :key="country" v-for="country in countries" :value="country.ID"> {{ country.Country }}</option>
        </select>
    <!-- </div> -->
    
    
</template>

<script>
export default {
    name: 'Countries',
    props: ['countries'],
    data() {
        return {
            selected: 0
        }
    },
    methods: {
        onChange() {
            const country = this.countries.find((item) => item.ID === this.selected)

            this.$emit('getCountry', country)
        },
    },
}
</script>
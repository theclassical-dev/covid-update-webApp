<template>
    <div class="text-center">
        <h2 class="text-3xl font-bold text-yellow-500 md:text-white">{{ text }}</h2>
        <div class="text-2xl text-yellow-200 md:text-white mt-4 mb-10">{{ timestamp }}</div>
    </div>
</template>

<script>
import moment from 'moment'

    export default {
        name: 'DataTitle',
        props: ['text', 'dataDate'],
        computed:{
            timestamp: function() {
                return moment(this.dataDate).format('MMM Do YYYY, h:mm:ss a')
            }
        }
    }
</script>
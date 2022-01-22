<template>

    <div class="grid md:grid-cols-3 gap-4">
        <!-- #1 div -->
        <div class="shadow-md bg-blue-100 p-10 text-center rounded">
            <h3 class="text-3xl text-blue-900 font-bold mb-4">Cases</h3>
            <div class="text-2xl mb-4">
                <span class="font-bold">New:</span>
                {{ numWithCommas(status.NewConfirmed) }}
            </div>
            <div class="text-2xl mb-4">
                <span class="font-bold">Total:</span>
                {{ numWithCommas(status.TotalConfirmed) }}
            </div>
        </div>

        <!-- #1 div -->
        <div class="shadow-md bg-blue-200 p-10 text-center rounded">
            <h3 class="text-3xl text-blue-900 font-bold mb-4">Deaths</h3>
            <div class="text-2xl mb-4">
                <span class="font-bold">New:</span>
                {{ numWithCommas(status.NewDeaths) }}
            </div>
            <div class="text-2xl mb-4">
                <span class="font-bold">Total:</span>
                {{ numWithCommas(status.TotalDeaths) }}
            </div>
        </div>

        <!-- #1 div -->
        <div class="shadow-md bg-blue-200 p-10 text-center rounded">
            <h3 class="text-3xl text-blue-900 font-bold mb-4">Recovery</h3>
            <div class="text-2xl mb-4">
                <span class="font-bold">New:</span>
                {{ numWithCommas(status.NewRecovered) }}
            </div>
            <div class="text-2xl mb-4">
                <span class="font-bold">Total:</span>
                {{ numWithCommas(status.TotalRecovered) }}
            </div>
        </div>
        
    </div>

</template>

<script>
export default {
    name: 'DataDiv',
    props: ['status'],
    methods: {
        numWithCommas(x) {
            return x.toString().replace(/\B(?=(\d{3})+(?!\d))/g, ',')
        }
    }
}
</script>
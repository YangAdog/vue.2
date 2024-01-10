<script>
export default {
    data() {
        return {
            weatherData:[],
        };
    },
    mounted() {
        fetch("https://opendata.cwa.gov.tw/api/v1/rest/datastore/F-C0032-001?Authorization=CWB-85BC1DC7-F417-4BD4-9CB7-03C730862EDC")
        .then(res => {
            return res.json();
        })
        .then(result => {
            console.log(result);
            this.weatherData = result.records.location
        });
    },
}
</script>

<template class="pt-3 w-full flex flex-wrap gap-3 justify-center">
    <div>
        <!-- {{ weatherData }} -->
        <weatherCard v-for="item in weatherData"  :key="item.id"  class="w-[20%] mb-5" :weather-place="item" />
    </div>
</template>

<style scoped="scss">
</style>
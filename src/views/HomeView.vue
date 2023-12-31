<template >
    <main class="container text-white">
        <div class="pt-4 mb-8 relative">
            <input 
                type="text" 
                v-model="searchQuery" 
                @input="getSearchResults" 
                class="py-2 px-1 w-full bg-transparent border-b focus:border-weather-secondary focus:outline-none focus:shadow-[0px_1px_0_0_#004E71]">
        </div>
    </main>
</template>
<script setup>
import {ref} from "vue";
import axios from "axios";

const mapboxAPIKey = "pk.eyJ1Ijoic2NvdGhpcyIsImEiOiJjaWp1Y2ltYmUwMDBicmJrdDQ4ZDBkaGN4In0.sbihZCZJ56-fsFNKHXF8YQ";
const mapboxSearchResults = ref(null);
const searchQuery = ref("");
const queryTimeOut = ref(null);

const getSearchResult = () => {
    clearTimeout(queryTimeOut.value);
    queryTimeOut.value = setTimeout(async() =>{
        if (searchQuery.value !== ""){
            const result = await axios.get(`https://api.mapbox.com/geocoding/v5/mapbox.places/${searchQuery.value}.json?access_token=${mapboxAPIKey}`)
            mapboxSearchResults.value = result.data.features;
            console.log(mapboxSearchResults.value);
            return ;
        }
        mapboxSearchResults.value = null;
    },300)
}
</script>

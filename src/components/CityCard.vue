<template>
    <div class="flex py-6 px-3 bg-weather-secondary rounded-md shadow-md cursor-pointer">
        <div class="flex flex-col flex-1">
            <h2 class="text-3xl">{{ city.city }}</h2>
            <h3>{{ city.state }}</h3>
        </div>

        <div class="flex flex-col gap-2">
            <p class="text-3xl self-end">
                {{ Math.round((city.weather.main.temp - 32) * 5 / 9) }}&deg;
            </p>
            <div class="flex gap-2">
                <span class="text-xs">
                    Max:
                    {{ Math.round((city.weather.main.temp_max - 32) * 5 / 9) }}&deg;
                </span>
                <span class="text-xs">
                    Min:
                    {{ Math.round((city.weather.main.temp_min - 32) * 5 / 9) }}&deg;
                </span>
            </div>
        </div>
    </div>
</template>
  
<script setup>
defineProps({
    city: {
        type: Object,
        default: () => { },
    },
});
</script>
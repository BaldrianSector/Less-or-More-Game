<script>
export default {
    props: ['country', 'info', 'value', 'flag', 'image', 'size', 'population']
}
</script>

<template>

    <div class="transform transition duration-200 hover:scale-125  rounded-lg shadow-lg h-72 w-56 hover:shadow-xl bg-white text-black">

        <div :style="{ backgroundImage: 'url(' + image + ')' }" class="bg-cover bg-center m-2 h-3/6 rounded-lg"></div>

        <div class="px-5 pt-2 flex flex-col">
            <div class="flex justify-between">
                <h2 class="font-semibold ">{{ country }}</h2>
                <h2 class="font-semibold select-none">{{ flag }}</h2>
            </div>
            <p class="text-sm text-gray-500 mt-3">{{ info }}</p>
        </div>
    </div>

</template>
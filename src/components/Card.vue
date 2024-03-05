<script>
export default {
    props: ['title', 'info', 'size', 'population']
}
</script>

<template>

    <div class="transform transition duration-200 hover:scale-110 rounded-lg shadow-lg h-52 w-56 hover:shadow-xl bg-white text-black">
    <div class="bg-gradient-to-br from-rose-100 via-purple-200 to-purple-200 m-2 h-3/6 rounded-lg"></div>

    <div class="px-5 pt-2 flex flex-col">
        <h2 class="font-semibold ">{{ title }}</h2>
        <p class="text-sm text-gray-500">{{ info }}</p>
    </div>
    </div>

</template>
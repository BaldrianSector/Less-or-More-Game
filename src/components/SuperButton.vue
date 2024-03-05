<script>
export default {
    props: ['title']
}
</script>

<template>
    <button style="padding: 1rem; background-color: black; color: #fff; border-radius: 1rem;">
        <slot></slot>
    </button>
</template>
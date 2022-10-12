<template>
    <div class="getter">
        <p>{{ id }}</p>
        <p>{{ name }}</p>
    </div>
</template>

<script>
    export default {
        name: "AppGetter",

        props: ["id", "name"]
    }
</script>

<style lang="scss" scoped>
    .getter{
        border: 1px solid seagreen;
        border-radius: 10px;
        display: flex;
        justify-content: center;
        flex-wrap: wrap;
        gap: 10px;
        padding: 25px;
        box-sizing: border-box;
        transition: 0.2s;

        &:hover{
            transform: translateY(-5px);
            box-shadow: rgba(100, 100, 111, 0.2) 0 7px 29px 0;
            cursor: pointer;
        }
    }
</style>
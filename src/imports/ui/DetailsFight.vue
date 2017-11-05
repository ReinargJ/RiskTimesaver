<template>
    <div class="result-details">
        <div>{{result.attRolls}}</div>
        <div>{{result.defRolls}}</div>
    </div>
</template>

<script>
export default {
    props: {
        result: {
            required: true,
            type: Object
        }
    }
}
</script>

<style lang="less" scoped>
@import "style/imports.less";
    .result-details {
        display: none;
        width: fit-content;
        padding: 10px;
        margin: auto;
        border: 1px @app-color solid;
    }


</style>
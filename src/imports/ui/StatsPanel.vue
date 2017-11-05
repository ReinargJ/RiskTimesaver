<template>
    <div>
        Prochains renforts: {{scale[currentRenforts]}}
        <button @click="nextRenforts">Suivant</button>
    </div>
</template>

<script>
export default {
    data(){
        return {
            currentRenforts: 0,
            scale: [
                6,
                8,
                10,
                12,
                15,
                20,
                25,
                30,
                35
            ]
        }
    },

    methods: {
        nextRenforts(){
            if(this.currentRenforts <8)
                this.currentRenforts++;
        }
    }
}
</script>

<style lang="less" scoped>

</style>
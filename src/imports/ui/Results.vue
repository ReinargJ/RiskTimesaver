<template>
    <div>
        <h3>Resultats</h3>
        <div class="winner-announce">
            <div v-if="winner=='att'" :class="'text-'+winner+' important'">L'attaque l'emporte ! </div>
            <div v-else-if="winner=='def'" :class="'text-'+winner+' important'">La défense l'emporte ! </div>
            <button @click="handleShow">
                <span v-if="showMore">Moins de détail</span>
                <span v-else>Plus de détail</span>
            </button>
        </div>
        
        <div v-if="showMore">
            <span class="text-att">Pertes attaque</span> -
            <span class="text-def">Pertes défense</span>
            <result v-for="(res, n) in results" :key="n" :value="res"></result>
        </div>
    </div>
</template>

<script>
import Result from './Result.vue';

export default {
    props: {
        winner: {
            required: true,
            type: String
        },
        results: {
            required: true,
            type: Array
        }
    },
    data() {
        return {
            showMore: false
        }
    },
    components: {
        Result
    },
    methods: {
        handleShow(){
            this.showMore = !this.showMore;
        }
    }
}
</script>

<style lang="less" scoped>
    .winner-announce > div {
        display: inline;
    }
</style>
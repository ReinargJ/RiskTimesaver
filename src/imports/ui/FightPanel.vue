<template>
    <div id="fight-panel">
        <div class="form-panel">
            <p >Nombre troupes (<span class="underline-red">Attaquant</span>) </p>
            <p>Limite</p>
            <input type="text" v-model="attacker" placeholder="entrez votre nombre de troupes" />

            <input type="text" v-model="limit" placeholder="limite de troupes" />
            <p>Nombre des troupes (<span class="underline-blue">Défenseur</span>) </p>
            <input type="text" v-model="defender" placeholder="entrez votre nombre de troupes" />
        </div>
        <div class="starting-block">
            <button @click="startBattle">Lancer la bataille !</button>
        </div>
    </div>
</template>

<script>

import Random from 'random-js';
import _ from 'lodash';

export default {
    props: {

    },

    data() {
        return {
            attacker: 15,
            defender: 15,
            generator: null,
            results: [],
            limit: 0,
            initialized: false,
            winner: "",
        }
    },

    methods: {
        initialize() {
            this.results = [];
            this.winner = "";

        },
        decreasingSort(a, b) {
            return b - a;
        },
        startBattle() {
            if (!this.initialized) {
                this.initialize();
            }
            while (this.attacker > this.limit && this.defender > 0) {
                let a = this.rollDice(3);
                let d = this.rollDice(2);

                let result = this.letMagicHappen(a, d)
            }

            if (this.attacker <= this.limit) {
                this.winner = "def";
            } else {
                this.winner = "att";
            }

            //fin du combat on remonte les données au parent pour les afficher"
            this.$emit('fightEnd', this.winner, this.results);
            this.initialized = false;
        },
        rollDice(nb) {
            let results = [];
            for (var i = 0; i < nb; i++) {
                results.push(this.generator.integer(1, 6));
            }
            return results;
        },
        letMagicHappen(att, def) {
            att.sort(this.decreasingSort);
            def.sort(this.decreasingSort);

            let outcome = {
                defLosses: 0,
                defRolls: def,
                attLosses: 0,
                attRolls: att
            };

            if (att.length > def.length) {
                def.forEach((roll, index) => {

                    if (att[index] > roll) {
                        console.log("att win");
                        outcome.defLosses++;
                        
                        this.defender=this.defender-1||0;
                    }
                    else {
                        console.log("def win");
                        outcome.attLosses++;
                        this.attacker=this.attacker-1||0;
                    }
                })
            } else {
                att.forEach((roll, index) => {
                    if (def[index] > roll) {
                        console.log("def win");
                        outcome.attLosses++;
                        this.attacker=this.attacker-1||0;
                    } else {
                        console.log("att win");
                        outcome.defLosses++;
                        this.defender=this.defender-1||0;
                    }
                })
            }

            this.results.push(outcome);
        },
    },

    created() {
        this.generator = new Random(Random.engines.mt19937().autoSeed());
        this.initialized = true;
    },
}
</script>

<style lang="less" scoped>
    .starting-block,
    .form-panel {
        margin-bottom: 10px;
    }


     .underline-blue {
        text-decoration: underline;
        text-decoration-color: #296C9B;
    }

    .underline-red {
        text-decoration: underline;
        text-decoration-color: red;
    }

    .form-panel {
        text-align: left;
    }
</style>


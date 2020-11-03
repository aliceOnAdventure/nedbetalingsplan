<template>
    <v-app>
        <v-data-table
            :headers="headers"
            :items="innbetalinger"
            class="elevation-1"
            hide-default-footer
            disable-pagination
        >
        </v-data-table>
    </v-app>
</template>

<script>
import axios from 'axios';
export default {
    name: 'Table',
    props: {
        laanebelop: {
            type: Number,
            default: 300000,
        },
        nominellRente: {
            type: Number,
            default: 3
        },
        terminGebyr: {
            type: Number,
            default: 30
        },
        utlopsDato: {
            type: String,
            default: '2045-01-01'
        },
        datoForsteInnbetaling: {
            type: String,
            default: '2020-01-01'
        },
        saldoDato: {
            type: String,
            default: '2020-02-01'
        },
    },
    computed: {
        /**
         * Used in order to listen to all the props
         */
        propertyAAndPropertyB() {
          return `${this.laanebelop}|${this.nominellRente}|${this.terminGebyr}|${this.utlopsDato}|${this.datoForsteInnbetaling}|${this.saldoDato}`;
        },
    },
    watch: {
        /**
         * When the prop changes, call loadData() to update the downpayment plan.
         */
        propertyAAndPropertyB(){
            this.loadData()
        } 
    },
    mounted() {
        this.loadData();
    },
    data() {
        return {
            innbetalinger: [],
            ukjentVerdi: 'TERMINBELOP',    
            headers: [
                { text: 'Dato', sortable: false, value: 'dato'},
                { text: 'Gebyr', sortable: false, value: 'gebyr'},
                { text: 'Innbetaling', sortable: false, value: 'innbetaling'},
                { text: 'Renter', sortable: false, value: 'renter'},
                { text: 'Restgjeld', sortable: false, value: 'restgjeld'},
                { text: 'Total', sortable: false, value: 'total'},
            ],
        }
    },

    methods: {
        /**
         *  Requests the downpayment plan by sending a POST request to the API.
         *  Then loads the plan into a table, which will update the UI.
         */
        async loadData() {
            await axios.post('https://visningsrom.stacc.com/dd_server_laaneberegning/rest/laaneberegning/v1/nedbetalingsplan', { 
                'laanebelop': this.laanebelop,
                'nominellRente': this.nominellRente,
                'terminGebyr': this.terminGebyr,
                'utlopsDato': this.utlopsDato,
                'saldoDato': this.saldoDato,
                'datoForsteInnbetaling': this.datoForsteInnbetaling,
                'ukjentVerdi': this.ukjentVerdi,
            }).then((response) => {
                this.innbetalinger = [];
                let innbetaling_data = response.data.nedbetalingsplan.innbetalinger;
                innbetaling_data.forEach(element => {
                    this.innbetalinger.push(element);
                });
            }).catch(function (error) {
                console.log("Error: ", error);
            });
        }
    },
}

</script>


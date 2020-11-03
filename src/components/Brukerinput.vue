<template>
    <v-app>
        <v-expansion-panels>
            <v-expansion-panel>
                <v-expansion-panel-header>
                    <template v-slot:default="{ open }">
                        <v-row no-gutters>
                        <v-col cols="4">
                            Informasjon om lånet
                        </v-col>
                        <v-col
                            cols="8"
                            class="text--secondary"
                        >
                            <v-fade-transition leave-absolute>
                            <span
                                v-if="open"
                                key="0"
                            >
                                Fyll inn informasjon om lånet
                            </span>
                            <span
                                v-else
                                key="1"
                            >
                            </span>
                            </v-fade-transition>
                        </v-col>
                        </v-row>
                    </template>
                </v-expansion-panel-header>
                <v-expansion-panel-content>
                    <template>
                        <v-form>
                            <v-container>
                                <v-row>
                                    <v-col
                                        cols="12"
                                        sm="6"
                                    >
                                        <v-text-field
                                            v-model="laanebelop"
                                            label="Lånebeløp"
                                            clearable
                                        >
                                        </v-text-field>
                                    </v-col>
            
                                    <v-col
                                        cols="12"
                                        sm="6"
                                    >
                                        <v-text-field
                                            v-model="nominellRente"
                                            label="Nominell rente"
                                            clearable
                                        ></v-text-field>
                                    </v-col>

                                    <v-col
                                        cols="12"
                                        sm="6"
                                    >
                                        <v-text-field
                                            v-model="terminGebyr"
                                            label="Termin gebyr"
                                            clearable
                                        ></v-text-field>
                                    </v-col>
                
                                    <v-col
                                        cols="12"
                                        sm="6"
                                        md="4"
                                    >
                                        <v-menu
                                        v-model="date_menu1"
                                        :close-on-content-click="false"
                                        :nudge-right="40"
                                        transition="scale-transition"
                                        offset-y
                                        min-width="290px"
                                        >
                                            <template v-slot:activator="{ on, attrs }">
                                                <v-text-field
                                                v-model="utlopsDato"
                                                label="Utløps dato"
                                                prepend-icon="mdi-calendar"
                                                readonly
                                                v-bind="attrs"
                                                v-on="on"
                                                ></v-text-field>
                                            </template>
                                            <v-date-picker
                                                color="rgb(135, 42, 34)"
                                                v-model="utlopsDato"
                                                @input="date_menu1 = false"
                                            ></v-date-picker>
                                        </v-menu>
                                    </v-col>

                                    <v-col
                                        cols="12"
                                        sm="6"
                                        md="4"
                                    >
                                        <v-menu
                                        v-model="date_menu2"
                                        :close-on-content-click="false"
                                        :nudge-right="40"
                                        transition="scale-transition"
                                        offset-y
                                        min-width="290px"
                                        >
                                            <template v-slot:activator="{ on, attrs }">
                                                <v-text-field
                                                v-model="saldoDato"
                                                label="Saldo dato"
                                                prepend-icon="mdi-calendar"
                                                readonly
                                                v-bind="attrs"
                                                v-on="on"
                                                ></v-text-field>
                                            </template>
                                            <v-date-picker
                                                color="rgb(135, 42, 34)"
                                                v-model="saldoDato"
                                                @input="date_menu2 = false"
                                            ></v-date-picker>
                                        </v-menu>
                                    </v-col>

                                    <v-col
                                        cols="12"
                                        sm="6"
                                        md="4"
                                    >
                                        <v-menu
                                        v-model="date_menu3"
                                        :close-on-content-click="false"
                                        :nudge-right="40"
                                        transition="scale-transition"
                                        offset-y
                                        min-width="290px"
                                        >
                                            <template v-slot:activator="{ on, attrs }">
                                                <v-text-field
                                                v-model="datoForesteInnbetaling"
                                                label="Dato for første innbetaling"
                                                prepend-icon="mdi-calendar"
                                                readonly
                                                v-bind="attrs"
                                                v-on="on"
                                                ></v-text-field>
                                            </template>
                                            <v-date-picker
                                                color="rgb(135, 42, 34)"
                                                v-model="datoForesteInnbetaling"
                                                @input="date_menu3 = false"
                                            ></v-date-picker>
                                        </v-menu>
                                    </v-col>
                                </v-row>
                            </v-container>
                        </v-form>
                    </template>
                </v-expansion-panel-content>
            </v-expansion-panel>
        </v-expansion-panels>
        <Tabell 
            :laanebelop=parseInt(laanebelop) 
            :nominellRente=parseInt(nominellRente)
            :terminGebyr=parseInt(terminGebyr) 
            :utlopsDato=utlopsDato 
            :datoForesteInnbetaling=datoForesteInnbetaling 
            :saldoDato=saldoDato
             />
    </v-app>
</template>

<script>
import Tabell from './Tabell';
export default {
    name: 'Brukerinput',
    components: {
        Tabell,
    },
    data() {
        return {
            laanebelop: 300000,
            nominellRente: 3,
            terminGebyr: 30,
            utlopsDato: '2045-01-01',
            saldoDato: '2020-01-01',
            datoForesteInnbetaling: '2020-02-01',
            visible: true,
            date_menu1: false,
            date_menu2: false,
            date_menu3: false,
        }
    },
}

</script>


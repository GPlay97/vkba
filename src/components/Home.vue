<template>
    <v-app>
        <Navigation />
        <v-content class="page-content" app>
            <v-container fill-height app>
                <v-layout app row>
                    <v-dialog persistent v-model="dialogPayin" max-width="500px">
                        <v-card>
                            <v-card-title class="headline theme--light" primary-title>Einzahlung</v-card-title>
                        </v-card>
                        <v-card-text class="white">
                            <v-layout justify-center>
                                <v-btn-toggle mandatory class="tab-selection-toggle">
                                    <v-btn flat class="tab-selection-btn" :ripple="false" @click="dialogPayinCredit = true; dialogPayinATM = false">Guthaben</v-btn>
                                    <v-btn flat class="tab-selection-btn" :ripple="false" @click="dialogPayinCredit = payinCreditForm = false; dialogPayinATM = true">Geldautomat</v-btn>
                                </v-btn-toggle>
                            </v-layout>
                            <v-layout justify-center>
                                <v-card-actions style="width: 100%">
                                    <v-btn class="tab-selection-btn" color="red" outline @click="dialogPayin = false">Abbrechen</v-btn>
                                    <v-btn class="tab-selection-btn" color="green" outline :disabled="!payinCreditForm && !dialogPayinATM">Bestätigen</v-btn>
                                </v-card-actions>
                            </v-layout>
                            <v-container grid-list-md v-if="dialogPayinCredit">
                                <v-layout wrap>
                                    <v-flex xs12>
                                        <span class="subheading">
                                            Guthaben kannst Du in der VKBA-Zentrale auf <b>Server 1</b> bei <b>/w Legend</b>
                                            erwerben.<br>
                                            Bitte gib den Code im unten stehenden Feld ein. <br>
                                            Das Guthaben wird Dir unmittelbar nach Einlösung gutgeschrieben.
                                        </span>
                                    </v-flex>
                                    <v-form style="width: 100%" v-model="payinCreditForm">
                                        <v-flex xs12>
                                            <v-text-field label="Code" v-model="payinCreditCode" required mask="credit-card"
                                                append-outer-icon="card_giftcard" hint="Gib Deinen 16-stelligen Guthaben-Code ein"
                                                :rules="[rules.credit]"></v-text-field>
                                        </v-flex>
                                    </v-form>
                                </v-layout>
                            </v-container>
                            <v-container grid-list-md v-if="dialogPayinATM">
                                <v-layout wrap>
                                    <v-flex xs12>
                                        <span class="subheading">
                                            Über die VKBA-Geldautomaten auf Server 1 bei /w Legend,
                                            kannst Du beliebiges Guthaben aufladen.<br>
                                            Benutze hierzu die verschiedenen zur Verfügungen stehenden Automaten,
                                            warte ein paar Minuten und drücke auf Bestätigen.<br>
                                            Nach erfolgter Erkennung wird Dir das eingezahlte Guthaben hier
                                            gutgeschrieben.<br>
                                            <i><b>Gegebenenfalls kommt es zu kurzen Verzögerungen bei der Erkennung.
                                                    Wenige Minuten später einfach erneut versuchen</b></i>
                                        </span>
                                    </v-flex>
                                </v-layout>
                            </v-container>
                        </v-card-text>
                    </v-dialog>
                    <v-flex xs12>
                        <v-container fluid grid-list-sm>
                            <v-layout row wrap>
                                <v-flex xs12 md6>
                                    <v-card class="mt-3 mx-auto dashboard-card" max-width="400">
                                        <v-sheet class="v-sheet--offset mx-auto dashboard-sheet" color="cyan" max-width="calc(100% - 32px)">
                                            <v-sparkline :labels="labels" :value="value" color="white" line-width="2"
                                                padding="16"></v-sparkline>
                                        </v-sheet>

                                        <v-card-text class="pt-0">
                                            <div class="title font-weight-light mb-2">Kontostand</div>
                                            <div class="subheading font-weight-bold grey--text">4.500, 56 Kadis</div>
                                            <v-divider class="my-2"></v-divider>
                                            <v-card-actions class="pa-3">
                                                <v-btn flat color="red" outline>Auszahlen</v-btn>
                                                <v-spacer></v-spacer>
                                                <v-btn flat color="green" outline @click="dialogPayin=true; payinCreditCode=''">Einzahlen</v-btn>
                                            </v-card-actions>
                                        </v-card-text>
                                    </v-card>
                                </v-flex>
                                <v-flex xs12 md6>
                                    <v-card class="mt-3 mx-auto dashboard-card" max-width="400">
                                        <v-sheet class="v-sheet--offset mx-auto dashboard-sheet" color="cyan" max-width="calc(100% - 32px)">
                                            <v-sparkline :labels="labels" :value="value" color="white" line-width="2"
                                                padding="16"></v-sparkline>
                                        </v-sheet>
                                        <v-card-text class="pt-0">
                                            <div class="title font-weight-light mb-2">QuickPoints</div>
                                            <div class="subheading font-weight-bold grey--text">12 QuickPoints</div>
                                            <v-divider class="my-2"></v-divider>
                                            <v-card-actions class="pa-3">
                                                <v-icon class="mr-2" small>
                                                    grade
                                                </v-icon>
                                                <span class="caption grey--text font-weight-light">durchschnittliche
                                                    Bewertung</span>
                                                <v-spacer></v-spacer>
                                                <v-icon>star</v-icon>
                                                <v-icon>star</v-icon>
                                                <v-icon>star</v-icon>
                                                <v-icon>star_half</v-icon>
                                                <v-icon>star_border</v-icon>
                                            </v-card-actions>
                                        </v-card-text>
                                    </v-card>
                                </v-flex>
                                <v-flex xs12 md6>
                                    <v-card class="mt-3 mx-auto dashboard-card" max-width="400">
                                        <v-sheet class="v-sheet--offset mx-auto dashboard-sheet" color="cyan" max-width="calc(100% - 32px)">
                                            <v-sparkline :labels="labels" :value="value" color="white" line-width="2"
                                                padding="16"></v-sparkline>
                                        </v-sheet>

                                        <v-card-text class="pt-0">
                                            <div class="title font-weight-light mb-2">Transaktionen</div>
                                            <div class="subheading font-weight-bold grey--text">17 Transaktionen (2
                                                heute)</div>
                                            <v-divider class="my-2"></v-divider>
                                            <v-card-actions class="pa-3">
                                                <v-btn flat color="primary" outline>Historie</v-btn>
                                                <v-spacer></v-spacer>
                                                <v-btn flat color="green" outline>Transaktion starten</v-btn>
                                            </v-card-actions>
                                        </v-card-text>
                                    </v-card>
                                </v-flex>
                                <v-flex xs12 md6>
                                    <v-card class="mt-3 mx-auto dashboard-card" max-width="400">
                                        <v-sheet class="v-sheet--offset mx-auto dashboard-sheet" color="cyan" max-width="calc(100% - 32px)">
                                            <v-sparkline :labels="labels" :value="value" color="white" line-width="2"
                                                padding="16"></v-sparkline>
                                        </v-sheet>

                                        <v-card-text class="pt-0">
                                            <div class="title font-weight-light mb-2">Kontakte</div>
                                            <div class="subheading font-weight-bold grey--text">4 Kontakte</div>
                                            <v-divider class="my-2"></v-divider>
                                            <v-card-actions class="pa-3">
                                                <v-btn flat color="primary" outline>Adressbuch</v-btn>
                                                <v-spacer></v-spacer>
                                                <v-btn flat color="green" outline>Kontakt hinzufügen</v-btn>
                                            </v-card-actions>
                                        </v-card-text>
                                    </v-card>
                                </v-flex>
                            </v-layout>
                        </v-container>
                    </v-flex>
                </v-layout>
            </v-container>
        </v-content>
    </v-app>
</template>

<script>
    import Navigation from './Navigation.vue';

    export default {
        data: () => ({
            dialogPayin: false,
            dialogPayinCredit: true,
            dialogPayinATM: false,
            payinCreditForm: false,
            payinCreditCode: '',
            rules: {
                credit: value => value && value.length === 16 && !isNaN(parseInt(value)) ||
                    'Code falsch oder unvollständig'
            },
            test: 'Test!',
            labels: [
                '12am',
                '3am',
                '6am',
                '9am',
                '12pm',
                '3pm',
                '6pm',
                '9pm'
            ],
            value: [
                200,
                675,
                410,
                390,
                310,
                460,
                250,
                240
            ]
        }),
        components: {
            Navigation
        }
    }
</script>

<style scoped>
    .dashboard-card {
        padding-top: 4px;
    }

    .dashboard-sheet {
        margin: 4px;
    }

    .tab-selection-toggle {
        width: 100%;
        box-shadow: none;
    }

    .tab-selection-btn {
        width: 50%;
    }

    .tab-selection-btn::before {
        background-color: white;
    }
</style>
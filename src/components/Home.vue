<template>
    <v-app>
        <Navigation />
        <v-content class="page-content" app>
            <v-container fill-height app>
                <v-layout app row>
                    <v-flex xs12>
                        <v-container fluid grid-list-sm>
                            <v-layout row wrap>
                                <v-flex xs6>
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
                                                <v-btn flat color="red">Auszahlen</v-btn>
                                                <v-spacer></v-spacer>
                                                <v-btn flat color="green">Einzahlen</v-btn>
                                            </v-card-actions>
                                        </v-card-text>
                                    </v-card>
                                </v-flex>
                                <v-flex xs6>
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
                                <v-flex xs6>
                                    <v-card class="mt-3 mx-auto dashboard-card" max-width="400">
                                        <v-sheet class="v-sheet--offset mx-auto dashboard-sheet" color="cyan" max-width="calc(100% - 32px)">
                                            <v-sparkline :labels="labels" :value="value" color="white" line-width="2"
                                                padding="16"></v-sparkline>
                                        </v-sheet>

                                        <v-card-text class="pt-0">
                                            <div class="title font-weight-light mb-2">Transaktionen</div>
                                            <div class="subheading font-weight-bold grey--text">17 Transaktionen (2 heute)</div>
                                            <v-divider class="my-2"></v-divider>
                                            <v-card-actions class="pa-3">
                                                <v-btn flat color="primary">Historie</v-btn>
                                                <v-spacer></v-spacer>
                                                <v-btn flat color="green">Transaktion starten</v-btn>
                                            </v-card-actions>
                                        </v-card-text>
                                    </v-card>
                                </v-flex>
                                <v-flex xs6>
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
                                                <v-btn flat color="primary">Adressbuch</v-btn>
                                                <v-spacer></v-spacer>
                                                <v-btn flat color="green">Kontakt hinzufügen</v-btn>
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
</style>
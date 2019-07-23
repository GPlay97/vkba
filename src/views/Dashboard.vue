<template>
    <v-container fluid grid-list-xl>
        <v-layout row wrap>
            <!-- Card Widgets -->
            <v-flex d-flex lg3 sm6 xs12>
                <widget-card icon="money" title="KAD 1.234,51" subTitle="+7% zu gestern" supTitle="Kontostand" color="#00b297" :actions="['Einzahlen', 'Auszahlen']" />
            </v-flex>
            <v-flex d-flex lg3 sm6 xs12>
                <widget-card icon="card_giftcard" title="74" subTitle="+3 heute" supTitle="QuickPoints" color="#dc3545" />
            </v-flex>
            <v-flex d-flex lg3 sm6 xs12>
                <widget-card icon="swap_horiz" title="123" subTitle="+4 heute" supTitle="Transaktionen" color="#0866C6" />
            </v-flex>
            <v-flex d-flex lg3 sm6 xs12>
                <widget-card icon="group" title="3" subTitle="+2 heute" supTitle="Kontakte" color="#1D2939" :actions="['Verwalten']"/>
            </v-flex>
            <!-- Transactions -->
            <v-flex d-flex lg6 sm6 xs12>
                <data-table title="Transaktionen" />
            </v-flex>
            <!-- Shop -->
            <v-flex d-flex lg6 sm6 xs12>
                <data-table title="Shop" />
            </v-flex>
        </v-layout>
    </v-container>
</template>

<script>
import widgetcard from '../components/WidgetCard.vue';
import datatable from '../components/DataTable.vue';

export default {
    components: {
        'widget-card': widgetcard,
        'data-table': datatable
    }
}
</script>


<template>
    <v-container fluid grid-list-xl>
        <payin-dialog :showDialog="showPayinDialog" />
        <payout-dialog :showDialog="showPayoutDialog" @cancelDialog="showPayoutDialog = false" @submitDialog="showPayoutDialog = false" />
        <v-layout row wrap>
            <!-- Card Widgets -->
            <v-flex d-flex lg3 sm6 xs12>
                <widget-card icon="money" title="KAD 1.234,51" subTitle="+7% zu gestern" supTitle="Kontostand" color="#00b297" :actions="['Einzahlen', 'Auszahlen']" @actionClicked="balanceHandler" />
            </v-flex>
            <v-flex d-flex lg3 sm6 xs12>
                <widget-card icon="card_giftcard" title="74" subTitle="+3 heute" supTitle="QuickPoints" color="#dc3545" :actions="['Prämienshop']"/>
            </v-flex>
            <v-flex d-flex lg3 sm6 xs12>
                <widget-card icon="swap_horiz" title="123" subTitle="+4 heute" supTitle="Transaktionen" color="#0866C6" :actions="['Überweisen']"/>
            </v-flex>
            <v-flex d-flex lg3 sm6 xs12>
                <widget-card icon="group" title="3" subTitle="+2 heute" supTitle="Kontakte" color="#1D2939" :actions="['Verwalten']"/>
            </v-flex>
            <!-- Transactions -->
            <v-flex d-flex lg6 sm6 xs12>
                <data-table title="Transaktionen" footerBtn="Käuferschutz"/>
            </v-flex>
            <!-- Shop -->
            <v-flex d-flex lg6 sm6 xs12>
                <data-table title="Shop" footerBtn="Verkaufen"/>
            </v-flex>
        </v-layout>
    </v-container>
</template>

<script>
import widgetCard from '../components/WidgetCard.vue';
import dataTable from '../components/DataTable.vue';
import payinDialog from '../components/dialogs/Payin.vue';
import payoutDialog from '../components/dialogs/Payout.vue';

export default {
    components: {
        'widget-card': widgetCard,
        'data-table': dataTable,
        'payin-dialog': payinDialog,
        'payout-dialog': payoutDialog
    },
    data: () => ({
        showPayinDialog: false,
        showPayoutDialog: false
    }),
    methods: {
        balanceHandler(action) {
            if (action === 'Auszahlen') this.showPayoutDialog = true;
        }
    }
}
</script>


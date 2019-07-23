<template>
    <v-card>
        <v-card-title>
            {{ title }}
            <v-spacer></v-spacer>
            <v-text-field v-model="search" append-icon="search" label="Suchen" single-line hide-details></v-text-field>
        </v-card-title>
        <v-data-table :headers="headers" :items="items" :search="search" rows-per-page-text="Einträge pro Seite" no-data-text="Keine Daten">
            <template v-slot:items="props">
                <td>{{ props.item.name }}</td>
                <td class="text-xs-right">{{ props.item.calories }}</td>
                <td class="text-xs-right">{{ props.item.fat }}</td>
                <td class="text-xs-right">{{ props.item.carbs }}</td>
                <td class="text-xs-right">{{ props.item.protein }}</td>
                <td class="text-xs-right">{{ props.item.iron }}</td>
            </template>
            <template v-slot:no-results>
                <v-alert :value="true" color="error" icon="warning">
                    Die Suche nach "{{ search }}" brachte keine Ergebnisse.
                </v-alert>
            </template>
            <template v-slot:footer v-if="footerBtn">
                <v-btn color="primary">
                    {{ footerBtn }}
                </v-btn>
            </template>
        </v-data-table>
    </v-card>
</template>

<script>
    export default {
        data: () => ({
            search: ''
        }),
        props: {
            title: {
                type: String,
                required: true
            },
            headers: {
                type: Array,
                required: false
            },
            items: {
                type: Array,
                required: false
            },
            footerBtn: {
                type: String,
                required: false
            }
        }
    }
</script>
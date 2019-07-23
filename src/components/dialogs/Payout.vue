<template>
    <v-dialog v-model="showDialog" persistent max-width="290">
        <v-card>
            <v-card-title class="headline">Auszahlen</v-card-title>
            <v-card-text>
                Du kannst Dir Deine Kadis von VKBA wieder auf Dein Spielerkonto auf Kadcon auszahlen lassen.
                Hierfür wird eine geringe Gebühr in Höhe von 5% fällig.
                Die Bearbeitung der Anfrage und Auszahlung beansprucht im Durschnitt bis zu 48h.
            </v-card-text>
            <v-card-actions>
                <v-btn flat @click="$emit('cancelDialog')">Abbrechen</v-btn>
                <v-btn flat color="orange" @click="$emit('submitDialog')">Auszahlen</v-btn>
            </v-card-actions>
        </v-card>
    </v-dialog>
</template>

<script>
export default {
    props: {
        showDialog: {
            type: Boolean,
            required: false
        }
    }
}
</script>

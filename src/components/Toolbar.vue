<template>
    <v-toolbar app>
        <v-toolbar-title class="headline text-uppercase">
            <span>VKBA</span>
            <span class="font-weight-light hidden-xs-only"> Virtuelle Konten für Kadcon</span>
        </v-toolbar-title>
        <v-spacer></v-spacer>
        <v-badge color="red" class="notification-badge">
            <template v-slot:badge>
                <p></p>
            </template>
            <v-btn icon>
                <v-icon>
                    notifications
                </v-icon>
            </v-btn>
        </v-badge>
        <v-btn icon>
            <v-avatar size="32px">
                <img src="https://minotar.net/avatar/LegendSkyFall" alt="Avatar">
            </v-avatar>
        </v-btn>
    </v-toolbar>
</template>

<style>
.notification-badge .v-badge__badge {
    width: 11px;
    height: 11px;
    right: 5px;
    top: 5px;
}
</style>


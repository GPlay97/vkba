<template>
    <v-navigation-drawer v-model="drawer" fixed  app>
        <v-toolbar flat class="toolbar">
            <v-list class="pa-0">
                <v-list-tile avatar>
                    <v-list-tile-avatar>
                        <img src="https://randomuser.me/api/portraits/men/85.jpg">
                    </v-list-tile-avatar>

                    <v-list-tile-content>
                        <v-list-tile-title>{{ username }}</v-list-tile-title>
                    </v-list-tile-content>
                </v-list-tile>
            </v-list>
        </v-toolbar>

        <v-divider></v-divider>

        <v-list dense class="pt-0">
            <v-list-tile v-for="item in items" :key="item.title" @click="openPage(item.page)">
                <v-list-tile-action>
                    <v-icon>{{ item.icon }}</v-icon>
                </v-list-tile-action>

                <v-list-tile-content>
                    <v-list-tile-title>{{ item.title }}</v-list-tile-title>
                </v-list-tile-content>
            </v-list-tile>
        </v-list>

        <v-footer class="pa-3" app>
            <v-spacer></v-spacer>
            <div>&copy; {{ new Date().getFullYear() }} VKBA</div>
        </v-footer>
    </v-navigation-drawer>
</template>

<script>
    export default {
        data: () => ({
            username: 'LegendSkyFall',
            drawer: true,
            items: [{
                    title: 'Home',
                    icon: 'dashboard',
                    page: '/home'
                },
                {
                    title: 'Transkationen',
                    icon: 'list',
                    page: '/transactions'
                },
                {
                    title: 'Kontakte',
                    icon: 'people',
                    page: '/contacts'
                },
                {
                    title: 'Shop',
                    icon: 'shop',
                    page: '/shop'
                },
                {
                    title: 'Abmelden',
                    icon: 'exit_to_app',
                    page: '/'
                }
            ]
        }),
        methods: {
            openPage(page) {
                this.$router.push(page);
            }
        }
    }
</script>
<template>
    <v-app>
        <v-app-bar>
            <v-toolbar-title>
                Welcome
            </v-toolbar-title>

            <v-spacer/>

            <InertiaLink  href="/login">
                <v-btn color="primary" >
                    Login
                </v-btn>
            </InertiaLink>

            <InertiaLink  href="/register">
                <v-btn>
                    Register
                </v-btn>
            </InertiaLink>
        </v-app-bar>
        <v-main>
           <v-container>
               <slot/>
           </v-container>
        </v-main>
    </v-app>
</template>

<script>
    export default {
        name:'GuestLayout'
    }
</script>

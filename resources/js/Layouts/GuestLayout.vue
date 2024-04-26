<template>
    <v-app>
        <v-app-bar>
            <v-toolbar-title>
                <InertiaLink class="InertiaLink" href="/">
                    Welcome
                </InertiaLink>
            </v-toolbar-title>

            <v-spacer/>

            <InertiaLink  href="/">
                <v-btn color="primary" >
                   <v-icon icon="mdi-home"/> Home
                </v-btn>
            </InertiaLink>

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

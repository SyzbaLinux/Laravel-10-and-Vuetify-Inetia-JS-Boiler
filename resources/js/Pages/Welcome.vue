<template>
    <div>
        <v-btn>
            Welcome
        </v-btn>
    </div>
</template>


<script>
    import GuestLayout from "@/Layouts/GuestLayout.vue";
    export default {

        layout:GuestLayout,
        watch: {
            $page: {
                handler() {
                    const message = this.$page.props.flash.message;
                    if (message != null) {
                        if(!message.optionRoute){
                            Swal.fire({
                                icon: message.type,
                                title: message.title,
                                text: message.description
                            })

                        }else{

                            Swal.fire({
                                title: message.title,
                                text:message.optiontext,
                                icon: message.type,
                                showCancelButton: true,
                                confirmButtonColor: '#42a848',
                                cancelButtonColor: '#d33',
                                cancelButtonText: 'Close',
                                confirmButtonText: 'Yes, Proceed'
                            }).then((result) => {
                                if (result.isConfirmed) {
                                    this.$inertia.visit(message.optionRoute)
                                }
                            })
                        }
                    }
                },
            },
        },

    }
</script>

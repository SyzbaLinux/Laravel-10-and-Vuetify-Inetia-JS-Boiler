<script setup>
import GuestLayout from '@/Layouts/GuestLayout.vue';
import InputError from '@/Components/InputError.vue';
import InputLabel from '@/Components/InputLabel.vue';
import PrimaryButton from '@/Components/PrimaryButton.vue';
import TextInput from '@/Components/TextInput.vue';
import { Head, useForm } from '@inertiajs/vue3';

defineProps({
    status: {
        type: String,
    },
});

const form = useForm({
    email: '',
});

const submit = () => {
    form.post(route('password.email'));
};
</script>

<template>
    <GuestLayout>
        <Head title="Forgot Password" />

        <form @submit.prevent="submit">
            <v-card class="glass mx-auto mt-10" max-width="500">
                <v-card-title class="text-center mt-5">
                    Forgot Password?
                </v-card-title>

                <p class="pa-5 text-center">
                    Forgot your password? No problem. Just let us know your email address and we will email you a password reset
                    link that will allow you to choose a new one.
                </p>

                <v-card-text>
                        <v-text-field
                            id="email"
                            type="email"
                            label="Email"
                            v-model="form.email"
                            required
                            autofocus
                            autocomplete="username"
                            :error-messages="form.errors.email"
                        />
                </v-card-text>

                <v-card-actions class="px-3 mb-5">
                    <v-btn type="submit" variant="flat" block size="x-large" :loading="form.processing">
                        Email Password Reset Link
                    </v-btn>
                </v-card-actions>
            </v-card>
        </form>
    </GuestLayout>
</template>

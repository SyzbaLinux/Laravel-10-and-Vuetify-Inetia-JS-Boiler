<script setup>
import GuestLayout from '@/Layouts/GuestLayout.vue';
import InputError from '@/Components/InputError.vue';
import InputLabel from '@/Components/InputLabel.vue';
import PrimaryButton from '@/Components/PrimaryButton.vue';
import TextInput from '@/Components/TextInput.vue';
import { Head, Link, useForm } from '@inertiajs/vue3';

const form = useForm({
    name: '',
    email: '',
    password: '',
    password_confirmation: '',
});

const submit = () => {
    form.post(route('register'), {
        onFinish: () => form.reset('password', 'password_confirmation'),
    });
};
</script>

<template>
    <GuestLayout>
        <Head title="Register" />

        <form @submit.prevent="submit">
            <v-card class="glass mt-10" max-width="550">
                <v-card-title class="my-3">
                    <h1>Register</h1>
                </v-card-title>

                <v-card-text>
                    <v-text-field
                        id="name"
                        label="Full Name"
                        v-model="form.name"
                        required
                        autofocus
                        autocomplete="name"
                        :error-messages="form.errors.name"
                    />

                    <v-text-field
                        type="email"
                        label="Email"
                        v-model="form.email"
                        required
                        autocomplete="username"
                        :error-messages="form.errors.email"
                    />

                    <v-text-field
                        type="password"
                        label="Password"
                        v-model="form.password"
                        required
                        autocomplete="username"
                        :error-messages="form.errors.password"
                    />

                    <v-text-field
                        type="password"
                        label="Confirm Password"
                        v-model="form.password_confirmation"
                        required
                        autocomplete="username"
                        :error-messages="form.errors.password_confirmation"
                    />
                </v-card-text>

                <v-card-actions>
                    <v-btn variant="flat" size="large" block type="submit"  :loading="form.processing">
                        Register
                    </v-btn>
                </v-card-actions>


                <v-card-text class="d-flex justify-center mt-3">
                    <Link
                        :href="route('login')"
                        class="underline text-sm text-gray-600 hover:text-gray-900 rounded-md focus:outline-none focus:ring-2 focus:ring-offset-2 focus:ring-indigo-500"
                    >
                        Already registered? Log In
                    </Link>
                </v-card-text>
            </v-card>



        </form>
    </GuestLayout>
</template>

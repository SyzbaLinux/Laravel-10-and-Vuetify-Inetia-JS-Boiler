<script setup>
import Checkbox from '@/Components/Checkbox.vue';
import GuestLayout from '@/Layouts/GuestLayout.vue';
import InputError from '@/Components/InputError.vue';
import InputLabel from '@/Components/InputLabel.vue';
import PrimaryButton from '@/Components/PrimaryButton.vue';
import TextInput from '@/Components/TextInput.vue';
import { Head, Link, useForm } from '@inertiajs/vue3';

defineProps({
    canResetPassword: {
        type: Boolean,
    },
    status: {
        type: String,
    },
});

const form = useForm({
    email: '',
    password: '',
    remember: false,
});

const submit = () => {
    form.post(route('login'), {
        onFinish: () => form.reset('password'),
    });
};
</script>

<template>
    <GuestLayout>
        <Head title="Log in" />
        <form @submit.prevent="submit">
        <v-card class="glass mt-10" max-width="500">
            <v-card-title class="my-3">
                <h1>Login</h1>
            </v-card-title>

            <v-card-text>
                <v-text-field
                    type="email"
                    label="Email"
                    v-model="form.email"
                    required
                    autofocus
                    autocomplete="username"
                    :error-messages="form.errors.email"
                />

                <v-text-field
                    type="password"
                    label="Password"
                    v-model="form.password"
                    required
                    autocomplete="current-password"
                    :error-messages="form.errors.password"
                />

                <div class="d-flex">
                    <div class="block mt-4">
                        <label class="flex items-center">
                            <Checkbox name="remember" v-model:checked="form.remember" />
                            <span class="ms-2 text-sm text-gray-600">Remember me</span>
                        </label>
                    </div>
                    <v-spacer/>

                    <div class="flex items-center justify-end mt-4">
                        <Link
                            v-if="canResetPassword"
                            :href="route('register')"
                          >
                            Dont have an account?
                        </Link>
                    </div>
                </div>


            </v-card-text>

            <v-card-actions>
                <v-btn variant="flat" size="large" block type="submit"  :loading="form.processing">
                    Log in
                </v-btn>
            </v-card-actions>
            <v-card-text class="d-flex justify-center mt-3">
                <InertiaLink
                    v-if="canResetPassword"
                    :href="route('password.request')"
                    class=" "
                >
                    Forgot your password? Reset It Now
                </InertiaLink>
            </v-card-text>
        </v-card>
        </form>
    </GuestLayout>
</template>

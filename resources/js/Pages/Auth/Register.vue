
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

        <div class="max-w-md mx-auto mt-10 p-6 bg-white rounded-lg shadow-md">
            <img src="/images/amazon-com-logo-1.svg" alt="Amazon Logo" />

            <h2 class="text-2xl font-semibold mb-6">Crear cuenta</h2>

            <form @submit.prevent="submit">
                <div class="mb-4">
                    <InputLabel for="name" value="Tu nombre" />
                    <TextInput
                        id="name"
                        type="text"
                        v-model="form.name"
                        required
                        autofocus
                        autocomplete="name"
                    />
                    <InputError :message="form.errors.name" class="mt-2" />
                </div>

                <div class="mb-4">
                    <InputLabel for="email" value="Correo electrónico" />
                    <TextInput
                        id="email"
                        type="email"
                        v-model="form.email"
                        required
                        autocomplete="username"
                    />
                    <InputError :message="form.errors.email" class="mt-2" />
                </div>

                <div class="mb-4">
                    <InputLabel for="password" value="Contraseña" />
                    <TextInput
                        id="password"
                        type="password"
                        v-model="form.password"
                        required
                        autocomplete="new-password"
                    />
                    <InputError :message="form.errors.password" class="mt-2" />
                    <p class="mt-1 text-xs text-gray-500">
                        Debe tener al menos 6 caracteres.
                    </p>
                </div>

                <div class="mb-6">
                    <InputLabel for="password_confirmation" value="Vuelve a escribir la contraseña" />
                    <TextInput
                        id="password_confirmation"
                        type="password"
                        v-model="form.password_confirmation"
                        required
                        autocomplete="new-password"
                    />
                    <InputError :message="form.errors.password_confirmation" class="mt-2" />
                </div>

                <PrimaryButton :class="{ 'opacity-25': form.processing }" :disabled="form.processing">
                    Crear tu cuenta de Amazon
                </PrimaryButton>
            </form>

            <p class="mt-4 text-xs text-gray-600">
                Al crear una cuenta, aceptas las Condiciones de Uso y el Aviso de Privacidad de Amazon.
            </p>

            <p class="mt-4 text-sm">
                ¿Ya tienes una cuenta?
                <Link :href="route('login')" class="text-blue-600 hover:underline">
                    Iniciar sesión
                </Link>
            </p>
        </div>
    </GuestLayout>
</template>

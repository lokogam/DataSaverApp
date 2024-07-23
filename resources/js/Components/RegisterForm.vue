<template>
    <div class="max-w-md mx-auto mt-10 p-6 bg-white rounded-lg shadow-md">
        <img
            src="path/to/amazon-logo.png"
            alt="Amazon"
            class="mb-6 mx-auto h-8"
        />
        <h2 class="text-2xl font-semibold mb-6">Crear cuenta</h2>
        <form @submit.prevent="submitForm">
            <div class="mb-4">
                <label
                    for="name"
                    class="block text-sm font-medium text-gray-700"
                    >Tu nombre</label
                >
                <input
                    v-model="form.name"
                    type="text"
                    id="name"
                    class="mt-1 block w-full rounded-md border-gray-300 shadow-sm focus:border-yellow-500 focus:ring focus:ring-yellow-200 focus:ring-opacity-50"
                    :class="{ 'border-red-500': errors.name }"
                />
                <p v-if="errors.name" class="mt-1 text-xs text-red-500">
                    {{ errors.name }}
                </p>
            </div>
            <div class="mb-4">
                <label
                    for="email"
                    class="block text-sm font-medium text-gray-700"
                    >Correo electrónico</label
                >
                <input
                    v-model="form.email"
                    type="email"
                    id="email"
                    class="mt-1 block w-full rounded-md border-gray-300 shadow-sm focus:border-yellow-500 focus:ring focus:ring-yellow-200 focus:ring-opacity-50"
                    :class="{ 'border-red-500': errors.email }"
                />
                <p v-if="errors.email" class="mt-1 text-xs text-red-500">
                    {{ errors.email }}
                </p>
            </div>
            <div class="mb-4">
                <label
                    for="password"
                    class="block text-sm font-medium text-gray-700"
                    >Contraseña</label
                >
                <input
                    v-model="form.password"
                    type="password"
                    id="password"
                    class="mt-1 block w-full rounded-md border-gray-300 shadow-sm focus:border-yellow-500 focus:ring focus:ring-yellow-200 focus:ring-opacity-50"
                    :class="{ 'border-red-500': errors.password }"
                />
                <p v-if="errors.password" class="mt-1 text-xs text-red-500">
                    {{ errors.password }}
                </p>
                <p class="mt-1 text-xs text-gray-500">
                    Debe tener al menos 6 caracteres.
                </p>
            </div>
            <div class="mb-6">
                <label
                    for="password_confirmation"
                    class="block text-sm font-medium text-gray-700"
                    >Vuelve a escribir la contraseña</label
                >
                <input
                    v-model="form.password_confirmation"
                    type="password"
                    id="password_confirmation"
                    class="mt-1 block w-full rounded-md border-gray-300 shadow-sm focus:border-yellow-500 focus:ring focus:ring-yellow-200 focus:ring-opacity-50"
                    :class="{ 'border-red-500': errors.password_confirmation }"
                />
                <p
                    v-if="errors.password_confirmation"
                    class="mt-1 text-xs text-red-500"
                >
                    {{ errors.password_confirmation }}
                </p>
            </div>
            <button
                type="submit"
                class="w-full py-2 px-4 border border-transparent rounded-md shadow-sm text-sm font-medium text-gray-900 bg-yellow-400 hover:bg-yellow-500 focus:outline-none focus:ring-2 focus:ring-offset-2 focus:ring-yellow-500"
            >
                Crear tu cuenta de Amazon
            </button>
        </form>
        <p class="mt-4 text-xs text-gray-600">
            Al crear una cuenta, aceptas las Condiciones de Uso y el Aviso de
            Privacidad de Amazon.
        </p>
        <p class="mt-4 text-sm">
            ¿Ya tienes una cuenta?
            <a href="#" class="text-blue-600 hover:underline">Iniciar sesión</a>
        </p>
    </div>
</template>

<script>
import { ref } from "vue";
import axios from "axios";

export default {
    setup() {
        const form = ref({
            name: "",
            email: "",
            password: "",
            password_confirmation: "",
        });

        const errors = ref({});

        const validateForm = () => {
            errors.value = {};
            if (!form.value.name)
                errors.value.name = "El nombre es obligatorio.";
            if (!form.value.email) {
                errors.value.email = "El correo electrónico es obligatorio.";
            } else if (!/\S+@\S+\.\S+/.test(form.value.email)) {
                errors.value.email = "El correo electrónico no es válido.";
            }
            if (!form.value.password)
                errors.value.password = "La contraseña es obligatoria.";
            else if (form.value.password.length < 6)
                errors.value.password =
                    "La contraseña debe tener al menos 6 caracteres.";
            if (form.value.password !== form.value.password_confirmation) {
                errors.value.password_confirmation =
                    "Las contraseñas no coinciden.";
            }
            return Object.keys(errors.value).length === 0;
        };

        const submitForm = async () => {
            if (!validateForm()) return;

            try {
                const response = await axios.post("/register", form.value);
                console.log(response.data);
                window.location.href = '/dashboard'
                //redirigir a dashboard con axiox

                // Manejar respuesta exitosa (por ejemplo, redirigir o mostrar mensaje)
            } catch (error) {
                console.error(error.response.data);
                // Manejar errores (por ejemplo, mostrar mensajes de error)
            }
        };

        return {
            form,
            errors,
            submitForm,
        };
    },
};
</script>

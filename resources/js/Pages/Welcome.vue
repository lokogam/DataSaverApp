<script setup>
import { Head, Link } from "@inertiajs/vue3";

defineProps({
    canLogin: {
        type: Boolean,
    },
    canRegister: {
        type: Boolean,
    },
});
</script>

<template>
    <Head title="Welcome" />
    <div class="bg-gray-50 text-black/50 dark:bg-black dark:text-white/50">
        <div
            class="relative min-h-screen flex flex-col items-center justify-center selection:bg-[#FF2D20] selection:text-white"
        >
            <div
                class="max-w-md mx-auto mt-10 p-6 bg-white rounded-lg shadow-md"
            >
                <div class="flex justify-center mb-6 ">
                    <img src="/images/amazon-com-logo-1.svg" alt="Amazon Logo" />
                </div>

                <h2 class="text-2xl font-semibold mb-6 text-center">
                    Opciones de cuenta
                </h2>

                <div v-if="canLogin" class="space-y-4">
                    <Link
                        v-if="$page.props.auth.user"
                        :href="route('dashboard')"
                        class="block w-full py-2 px-4 border border-transparent rounded-md shadow-sm text-sm font-medium text-gray-900 bg-yellow-400 hover:bg-yellow-500 focus:outline-none focus:ring-2 focus:ring-offset-2 focus:ring-yellow-500 text-center"
                    >
                        Dashboard
                    </Link>

                    <template v-else>
                        <Link
                            :href="route('login')"
                            class="block w-full py-2 px-4 border border-transparent rounded-md shadow-sm text-sm font-medium text-gray-900 bg-yellow-400 hover:bg-yellow-500 focus:outline-none focus:ring-2 focus:ring-offset-2 focus:ring-yellow-500 text-center"
                        >
                            Iniciar sesión
                        </Link>

                        <Link
                            v-if="canRegister"
                            :href="route('register')"
                            class="block w-full py-2 px-4 border border-gray-300 rounded-md shadow-sm text-sm font-medium text-gray-700 bg-white hover:bg-gray-50 focus:outline-none focus:ring-2 focus:ring-offset-2 focus:ring-yellow-500 text-center"
                        >
                            Crear cuenta nueva
                        </Link>
                    </template>
                </div>

                <p class="mt-4 text-xs text-gray-600 text-center">
                    Al continuar, aceptas las Condiciones de Uso y el Aviso de
                    Privacidad.
                </p>
            </div>
        </div>
    </div>
</template>

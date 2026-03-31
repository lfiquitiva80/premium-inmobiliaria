<script setup lang="ts">
import { dashboard, login, register } from '@/routes';
import { Head, Link } from '@inertiajs/vue3';
import { 
    Building2, 
    Home, 
    HandCoins, 
    ArrowRight, 
    ShieldCheck, 
    Banknote, 
    MapPin, 
    Menu, 
    X 
} from 'lucide-vue-next';
import { ref } from 'vue';

withDefaults(
    defineProps<{
        canRegister: boolean;
    }>(),
    {
        canRegister: true,
    },
);

const isMenuOpen = ref(false);

const toggleMenu = () => {
    isMenuOpen.value = !isMenuOpen.value;
};
</script>

<template>
    <Head title="Premium Inmobiliaria">
        <link rel="preconnect" href="https://rsms.me/" />
        <link rel="stylesheet" href="https://rsms.me/inter/inter.css" />
    </Head>
    
    <div class="min-h-screen bg-slate-50 text-slate-900 font-sans selection:bg-indigo-500 selection:text-white dark:bg-slate-950 dark:text-slate-100">
        
        <!-- Navbar -->
        <nav class="fixed top-0 left-0 w-full z-50 bg-white/80 backdrop-blur-md border-b border-slate-200/50 dark:bg-slate-950/80 dark:border-slate-800/50 transition-all duration-300">
            <div class="max-w-7xl mx-auto px-4 sm:px-6 lg:px-8">
                <div class="flex justify-between h-20 items-center">
                    <div class="flex-shrink-0 flex items-center gap-2">
                        <div class="w-10 h-10 rounded-xl bg-gradient-to-br from-indigo-500 to-indigo-700 flex items-center justify-center text-white shadow-lg shadow-indigo-500/30">
                            <Building2 class="w-6 h-6" />
                        </div>
                        <span class="font-bold text-xl tracking-tight text-slate-800 dark:text-slate-100">Premium<span class="text-indigo-600 dark:text-indigo-400">Inmuebles</span></span>
                    </div>
                    
                    <!-- Desktop Menu -->
                    <div class="hidden md:flex space-x-8 items-center">
                        <a href="#nueva" class="text-sm font-medium text-slate-600 hover:text-indigo-600 transition-colors dark:text-slate-300 dark:hover:text-indigo-400">Vivienda Nueva</a>
                        <a href="#usada" class="text-sm font-medium text-slate-600 hover:text-indigo-600 transition-colors dark:text-slate-300 dark:hover:text-indigo-400">Vivienda Usada</a>
                        <a href="#cartera" class="text-sm font-medium text-slate-600 hover:text-indigo-600 transition-colors dark:text-slate-300 dark:hover:text-indigo-400">Compra de Cartera</a>
                        
                        <div class="block h-6 w-px bg-slate-200 dark:bg-slate-700"></div>
                        
                        <template v-if="$page.props.auth.user">
                            <Link :href="dashboard()" class="inline-flex items-center justify-center px-5 py-2.5 text-sm font-medium rounded-lg bg-indigo-600 text-white hover:bg-indigo-700 transition-all shadow-md hover:shadow-lg shadow-indigo-600/20 active:scale-95">
                                Dashboard
                            </Link>
                        </template>
                        <template v-else>
                            <Link :href="login()" class="text-sm font-medium text-slate-600 hover:text-indigo-600 transition-colors dark:text-slate-300 dark:hover:text-indigo-400">
                                Iniciar Sesión
                            </Link>
                            <Link v-if="canRegister" :href="register()" class="inline-flex items-center justify-center px-5 py-2.5 text-sm font-medium rounded-lg bg-indigo-600 text-white hover:bg-indigo-700 transition-all shadow-md hover:shadow-lg shadow-indigo-600/20 active:scale-95">
                                Regístrate
                            </Link>
                        </template>
                    </div>

                    <!-- Mobile menu button -->
                    <div class="flex items-center md:hidden">
                        <button @click="toggleMenu" class="text-slate-500 hover:text-slate-700 focus:outline-none dark:text-slate-400 dark:hover:text-slate-200">
                            <Menu v-if="!isMenuOpen" class="w-6 h-6" />
                            <X v-else class="w-6 h-6" />
                        </button>
                    </div>
                </div>
            </div>
            
            <!-- Mobile Menu -->
            <div v-show="isMenuOpen" class="md:hidden absolute w-full bg-white dark:bg-slate-900 shadow-xl border-b border-slate-200 dark:border-slate-800 transition-all">
                <div class="px-4 pt-2 pb-6 space-y-2">
                    <a @click="toggleMenu" href="#nueva" class="block px-3 py-3 rounded-md text-base font-medium text-slate-700 hover:text-indigo-600 hover:bg-slate-50 dark:text-slate-200 dark:hover:bg-slate-800">Vivienda Nueva</a>
                    <a @click="toggleMenu" href="#usada" class="block px-3 py-3 rounded-md text-base font-medium text-slate-700 hover:text-indigo-600 hover:bg-slate-50 dark:text-slate-200 dark:hover:bg-slate-800">Vivienda Usada</a>
                    <a @click="toggleMenu" href="#cartera" class="block px-3 py-3 rounded-md text-base font-medium text-slate-700 hover:text-indigo-600 hover:bg-slate-50 dark:text-slate-200 dark:hover:bg-slate-800">Compra de Cartera</a>
                    
                    <div class="pt-4 border-t border-slate-200 dark:border-slate-700"></div>
                    
                    <template v-if="$page.props.auth.user">
                        <Link :href="dashboard()" class="block w-full text-center px-4 py-3 border border-transparent text-base font-medium rounded-md text-white bg-indigo-600 hover:bg-indigo-700">
                            Dashboard
                        </Link>
                    </template>
                    <template v-else>
                        <Link :href="login()" class="block w-full text-center px-4 py-3 border border-slate-300 dark:border-slate-700 text-base font-medium rounded-md text-slate-700 dark:text-slate-200 bg-white dark:bg-slate-800 hover:bg-slate-50 dark:hover:bg-slate-700 mb-2">
                            Iniciar Sesión
                        </Link>
                        <Link v-if="canRegister" :href="register()" class="block w-full text-center px-4 py-3 border border-transparent text-base font-medium rounded-md text-white bg-indigo-600 hover:bg-indigo-700">
                            Regístrate
                        </Link>
                    </template>
                </div>
            </div>
        </nav>

        <!-- Hero Section -->
        <main class="relative pt-32 pb-16 md:pt-48 md:pb-32 overflow-hidden flex items-center min-h-[90vh]">
            <!-- Creative background elements -->
            <div class="absolute inset-0 z-0">
                <div class="absolute -top-40 -right-40 w-[600px] h-[600px] bg-indigo-500/10 rounded-full blur-3xl opacity-50 dark:opacity-20 pointer-events-none"></div>
                <div class="absolute top-40 -left-60 w-[700px] h-[700px] bg-cyan-500/10 rounded-full blur-3xl opacity-50 dark:opacity-20 pointer-events-none"></div>
                <div class="absolute bottom-0 right-1/4 w-[500px] h-[500px] bg-blue-500/10 rounded-full blur-3xl opacity-50 dark:opacity-20 pointer-events-none"></div>
                <div class="absolute inset-0 bg-[url('https://grainy-gradients.vercel.app/noise.svg')] opacity-[0.03] dark:opacity-[0.05] pointer-events-none mix-blend-overlay"></div>
            </div>

            <div class="relative z-10 max-w-7xl mx-auto px-4 sm:px-6 lg:px-8 w-full flex flex-col md:flex-row items-center gap-12 lg:gap-24">
                <div class="flex-1 text-center md:text-left">
                    <div class="inline-flex items-center rounded-full px-3 py-1 text-sm font-semibold text-indigo-600 dark:text-indigo-400 bg-indigo-100/50 dark:bg-indigo-900/30 ring-1 ring-inset ring-indigo-600/20 mb-6 backdrop-blur-sm">
                        <span class="flex h-2 w-2 rounded-full bg-indigo-600 dark:bg-indigo-400 mr-2 animate-pulse"></span>
                        Expertos Inmobiliarios
                    </div>
                    <h1 class="text-5xl md:text-6xl lg:text-7xl font-extrabold tracking-tight text-slate-900 dark:text-white leading-[1.1] mb-6">
                        Encuentra el hogar <br class="hidden md:block"/>
                        <span class="text-transparent bg-clip-text bg-gradient-to-r from-indigo-600 to-cyan-500">de tus sueños</span>
                    </h1>
                    <p class="mt-4 text-xl text-slate-600 dark:text-slate-300 max-w-2xl mx-auto md:mx-0 mb-10 leading-relaxed font-light">
                        Te acompañamos en cada paso. Ya sea que busques vivienda nueva, usada o necesites optimizar tu crédito con nuestra compra de cartera.
                    </p>
                    <div class="flex flex-col sm:flex-row gap-4 justify-center md:justify-start">
                        <a href="#nueva" class="inline-flex justify-center items-center py-4 px-8 text-base font-semibold rounded-xl text-white bg-indigo-600 hover:bg-indigo-700 shadow-xl shadow-indigo-600/20 hover:shadow-indigo-600/30 transition-all active:scale-95 group">
                            Ver Propiedades
                            <ArrowRight class="ml-2 w-5 h-5 group-hover:translate-x-1 transition-transform" />
                        </a>
                        <a href="#cartera" class="inline-flex justify-center items-center py-4 px-8 text-base font-semibold rounded-xl text-slate-700 dark:text-slate-200 bg-white dark:bg-slate-900 border border-slate-200 dark:border-slate-800 hover:bg-slate-50 dark:hover:bg-slate-800 hover:border-slate-300 dark:hover:border-slate-700 transition-all shadow-sm active:scale-95 group">
                            Estudio de Cartera
                        </a>
                    </div>
                    
                    <div class="mt-12 flex items-center justify-center md:justify-start gap-8 opacity-70 grayscale">
                        <div class="font-bold text-xl tracking-tighter">Bancolombia</div>
                        <div class="font-bold text-xl tracking-tighter">Davivienda</div>
                        <div class="font-bold text-xl tracking-tighter">Colpatria</div>
                    </div>
                </div>

                <div class="flex-1 w-full max-w-lg md:max-w-none relative">
                    <!-- Premium Glass Morphism Card Container -->
                    <div class="relative w-full aspect-[4/5] md:aspect-square lg:aspect-[4/5] rounded-[2.5rem] overflow-hidden bg-slate-200 dark:bg-slate-800 shadow-2xl group">
                        <!-- Simulated Image Background -->
                        <div class="absolute inset-0 bg-[url('https://images.unsplash.com/photo-1600596542815-ffad4c1539a9?ixlib=rb-4.0.3&auto=format&fit=crop&w=1200&q=80')] bg-cover bg-center transition-transform duration-1000 group-hover:scale-105"></div>
                        <div class="absolute inset-0 bg-gradient-to-t from-slate-900/90 via-slate-900/20 to-transparent"></div>
                        
                        <!-- Floating Info Card -->
                        <div class="absolute bottom-8 left-8 right-8 bg-white/10 dark:bg-slate-900/40 backdrop-blur-xl border border-white/20 dark:border-slate-700/50 p-6 rounded-3xl shadow-2xl">
                            <div class="flex justify-between items-start mb-4">
                                <div>
                                    <h3 class="text-white font-bold text-xl drop-shadow-md">Villa Contemporánea</h3>
                                    <p class="text-slate-200 text-sm flex items-center gap-1 mt-1">
                                        <MapPin class="w-4 h-4" /> Zona Norte, Ciudad
                                    </p>
                                </div>
                                <span class="bg-indigo-600 text-white text-xs font-bold px-3 py-1.5 rounded-full shadow-lg">Nueva</span>
                            </div>
                            <div class="flex justify-between items-center text-white">
                                <div>
                                    <p class="text-slate-300 text-xs uppercase tracking-wider font-semibold">Precio desde</p>
                                    <p class="font-extrabold text-2xl drop-shadow-md">$450M</p>
                                </div>
                                <button class="w-10 h-10 rounded-full bg-white text-indigo-600 flex items-center justify-center hover:bg-slate-50 transition-colors shadow-lg">
                                    <ArrowRight class="w-5 h-5 -rotate-45" />
                                </button>
                            </div>
                        </div>
                    </div>
                    
                    <!-- Decorative floating element -->
                    <div class="absolute -right-6 top-1/4 bg-white dark:bg-slate-800 p-4 rounded-2xl shadow-xl shadow-slate-200/50 dark:shadow-slate-900/50 border border-slate-100 dark:border-slate-700 flex items-center gap-4 animate-[bounce_5s_ease-in-out_infinite]">
                        <div class="w-12 h-12 bg-emerald-100 dark:bg-emerald-900/30 rounded-full flex items-center justify-center text-emerald-600 dark:text-emerald-400">
                            <ShieldCheck class="w-6 h-6" />
                        </div>
                        <div>
                            <p class="text-xs text-slate-500 dark:text-slate-400 font-medium tracking-wide">Transacción</p>
                            <p class="text-slate-800 dark:text-white font-bold text-sm">100% Segura</p>
                        </div>
                    </div>
                </div>
            </div>
        </main>

        <!-- Services Section -->
        <section class="py-24 bg-white dark:bg-slate-900 relative">
            <div class="max-w-7xl mx-auto px-4 sm:px-6 lg:px-8">
                <div class="text-center max-w-3xl mx-auto mb-16">
                    <h2 class="text-indigo-600 dark:text-indigo-400 font-semibold tracking-wide uppercase text-sm mb-3">Nuestras Soluciones</h2>
                    <h3 class="text-3xl md:text-5xl font-extrabold text-slate-900 dark:text-white mb-6">Todo lo que necesitas en un solo lugar</h3>
                    <p class="text-lg text-slate-600 dark:text-slate-400">Desde la búsqueda de tu primera casa hasta la optimización de tus finanzas, estamos contigo.</p>
                </div>

                <div class="grid md:grid-cols-3 gap-8">
                    <!-- Vivienda Nueva -->
                    <div id="nueva" class="group bg-slate-50 dark:bg-slate-800/50 rounded-3xl p-8 border border-slate-200/60 dark:border-slate-700/50 hover:bg-white dark:hover:bg-slate-800 hover:shadow-2xl hover:shadow-indigo-500/10 transition-all duration-300 relative overflow-hidden">
                        <div class="absolute top-0 right-0 w-32 h-32 bg-indigo-500/10 dark:bg-indigo-500/20 rounded-bl-full -mr-16 -mt-16 transition-transform group-hover:scale-110"></div>
                        <div class="w-16 h-16 bg-white dark:bg-slate-900 rounded-2xl shadow-sm border border-slate-100 dark:border-slate-700 flex items-center justify-center text-indigo-600 dark:text-indigo-400 mb-8 relative z-10 group-hover:scale-110 transition-transform duration-300">
                            <Building2 class="w-8 h-8" stroke-width="1.5" />
                        </div>
                        <h4 class="text-2xl font-bold text-slate-900 dark:text-white mb-4 relative z-10">Vivienda Nueva</h4>
                        <p class="text-slate-600 dark:text-slate-400 mb-8 leading-relaxed relative z-10">
                            Proyectos sobre planos y listos para entrega. Descubre diseños modernos, acabados premium y las mejores ubicaciones para estrenar.
                        </p>
                        <a href="#" class="inline-flex items-center font-semibold text-indigo-600 dark:text-indigo-400 hover:text-indigo-700 dark:hover:text-indigo-300 relative z-10 group-hover:translate-x-2 transition-transform">
                            Explorar proyectos
                            <ArrowRight class="ml-2 w-4 h-4" />
                        </a>
                    </div>

                    <!-- Vivienda Usada -->
                    <div id="usada" class="group bg-slate-50 dark:bg-slate-800/50 rounded-3xl p-8 border border-slate-200/60 dark:border-slate-700/50 hover:bg-white dark:hover:bg-slate-800 hover:shadow-2xl hover:shadow-cyan-500/10 transition-all duration-300 relative overflow-hidden">
                        <div class="absolute top-0 right-0 w-32 h-32 bg-cyan-500/10 dark:bg-cyan-500/20 rounded-bl-full -mr-16 -mt-16 transition-transform group-hover:scale-110"></div>
                        <div class="w-16 h-16 bg-white dark:bg-slate-900 rounded-2xl shadow-sm border border-slate-100 dark:border-slate-700 flex items-center justify-center text-cyan-600 dark:text-cyan-400 mb-8 relative z-10 group-hover:scale-110 transition-transform duration-300">
                            <Home class="w-8 h-8" stroke-width="1.5" />
                        </div>
                        <h4 class="text-2xl font-bold text-slate-900 dark:text-white mb-4 relative z-10">Vivienda Usada</h4>
                        <p class="text-slate-600 dark:text-slate-400 mb-8 leading-relaxed relative z-10">
                            Propiedades con historia en los barrios más consolidados. Mayor área por mejor precio. Inmuebles verificados listos para habitar.
                        </p>
                        <a href="#" class="inline-flex items-center font-semibold text-cyan-600 dark:text-cyan-400 hover:text-cyan-700 dark:hover:text-cyan-300 relative z-10 group-hover:translate-x-2 transition-transform">
                            Ver inventario
                            <ArrowRight class="ml-2 w-4 h-4" />
                        </a>
                    </div>

                    <!-- Compra de Cartera -->
                    <div id="cartera" class="group bg-slate-50 dark:bg-slate-800/50 rounded-3xl p-8 border border-slate-200/60 dark:border-slate-700/50 hover:bg-white dark:hover:bg-slate-800 hover:shadow-2xl hover:shadow-emerald-500/10 transition-all duration-300 relative overflow-hidden">
                        <div class="absolute top-0 right-0 w-32 h-32 bg-emerald-500/10 dark:bg-emerald-500/20 rounded-bl-full -mr-16 -mt-16 transition-transform group-hover:scale-110"></div>
                        <div class="w-16 h-16 bg-white dark:bg-slate-900 rounded-2xl shadow-sm border border-slate-100 dark:border-slate-700 flex items-center justify-center text-emerald-600 dark:text-emerald-400 mb-8 relative z-10 group-hover:scale-110 transition-transform duration-300">
                            <Banknote class="w-8 h-8" stroke-width="1.5" />
                        </div>
                        <h4 class="text-2xl font-bold text-slate-900 dark:text-white mb-4 relative z-10">Compra de Cartera</h4>
                        <p class="text-slate-600 dark:text-slate-400 mb-8 leading-relaxed relative z-10">
                            Mejora las condiciones de tu crédito hipotecario actual. Reducimos tu tasa de interés y cuota mensual con las mejores entidades financieras.
                        </p>
                        <a href="#" class="inline-flex items-center font-semibold text-emerald-600 dark:text-emerald-400 hover:text-emerald-700 dark:hover:text-emerald-300 relative z-10 group-hover:translate-x-2 transition-transform">
                            Calcula tu ahorro
                            <ArrowRight class="ml-2 w-4 h-4" />
                        </a>
                    </div>
                </div>
            </div>
        </section>

        <!-- CTA Section -->
        <section class="py-24 relative overflow-hidden">
            <div class="absolute inset-0 bg-indigo-600 dark:bg-indigo-900"></div>
            <div class="absolute inset-0 bg-[url('https://grainy-gradients.vercel.app/noise.svg')] opacity-20 mix-blend-overlay"></div>
            <div class="absolute -top-40 -right-40 w-96 h-96 bg-indigo-500 rounded-full blur-3xl opacity-50"></div>
            
            <div class="relative max-w-4xl mx-auto px-4 sm:px-6 lg:px-8 text-center z-10">
                <h2 class="text-3xl md:text-5xl font-extrabold text-white mb-6">¿Listo para dar el gran paso?</h2>
                <p class="text-xl text-indigo-100 mb-10 max-w-2xl mx-auto font-light">
                    Nuestros asesores están listos para guiarte sin compromiso. Déjanos tus datos y te contactaremos de inmediato.
                </p>
                <form @submit.prevent class="flex flex-col sm:flex-row gap-4 justify-center max-w-xl mx-auto">
                    <input type="email" placeholder="Tu correo electrónico" class="w-full sm:flex-1 px-6 py-4 rounded-xl bg-white/10 dark:bg-slate-900/40 border border-white/20 text-white placeholder-indigo-200 focus:outline-none focus:ring-2 focus:ring-white/50 backdrop-blur-md" required />
                    <button type="submit" class="px-8 py-4 rounded-xl font-bold text-indigo-900 bg-white hover:bg-indigo-50 transition-colors shadow-xl">
                        Asesoría Gratuita
                    </button>
                </form>
            </div>
        </section>

        <!-- Footer -->
        <footer class="bg-slate-50 dark:bg-slate-950 py-12 border-t border-slate-200 dark:border-slate-800">
            <div class="max-w-7xl mx-auto px-4 sm:px-6 lg:px-8 flex flex-col md:flex-row justify-between items-center gap-6">
                <div class="flex items-center gap-2">
                    <Building2 class="w-6 h-6 text-indigo-600 dark:text-indigo-400" />
                    <span class="font-bold text-xl tracking-tight text-slate-800 dark:text-slate-100">Premium<span class="text-indigo-600 dark:text-indigo-400">Inmuebles</span></span>
                </div>
                <div class="flex gap-6">
                    <a href="#" class="text-sm text-slate-500 hover:text-indigo-600 dark:text-slate-400 dark:hover:text-indigo-400">Términos y Condiciones</a>
                    <a href="#" class="text-sm text-slate-500 hover:text-indigo-600 dark:text-slate-400 dark:hover:text-indigo-400">Política de Privacidad</a>
                </div>
                <p class="text-sm text-slate-500 dark:text-slate-400">
                    &copy; 2026 Premium Inmuebles. Todos los derechos reservados.
                </p>
            </div>
        </footer>
    </div>
</template>

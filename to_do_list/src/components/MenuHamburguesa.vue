<template>
    <div class="menu-hamburguesa">

        <button @click="mostrarMenu = !mostrarMenu" class="hamburguesa" aria-label="Abrir menú">
            &#9776; <!-- Icono hamburguesa -->
        </button>
        <!-- Fondo oscuro para cerrar el menú al hacer clic fuera -->
        <div v-if="mostrarMenu" class="fondo-menu" @click="cerrarMenu"></div>

        <ul v-if="mostrarMenu" class="menu-lista">
            <li @click="cambiarFiltro('todas')">Ver todas las tareas</li>
            <li @click="cambiarFiltro('pendientes')">Ver tareas pendientes</li>
            <li @click="cambiarFiltro('completadas')">Ver tareas completadas</li>
        </ul>
    </div>
</template>

<script>
    export default {
        data() {
            return {
                mostrarMenu: false
            };
        },
        methods: {
            cambiarFiltro(filtro) {
                this.$emit('cambiar-filtro', filtro);
                this.mostrarMenu = false;
            },
            cerrarMenu() {
                this.mostrarMenu = false; // Cerrar el menú al hacer clic fuera
            }
        }
    };
</script>
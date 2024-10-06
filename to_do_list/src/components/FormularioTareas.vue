<template>
    <div class="formulario-tareas">
        <input v-model="nuevaTarea" placeholder="Agregar nueva tarea" />
        <button @click="agregarTarea">Agregar</button>
    </div>
</template>

<script>
    export default {
        data() {
            return {
                nuevaTarea: ''
            };
        },
        methods: {
            agregarTarea() {
                this.$emit('tarea-agregada', this.nuevaTarea);
                this.nuevaTarea = '';
            }
        }
    };
</script>

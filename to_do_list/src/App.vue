<template>
    <div id="app">
        <FormularioTareas @tarea-agregada="agregarTarea" />
        <ListaTareas :tareas="tareas" @tarea-eliminada="eliminarTarea" />
    </div>
</template>

<script>
    import FormularioTareas from './components/FormularioTareas.vue';
    import ListaTareas from './components/ListaTareas.vue';

    export default {
        components: {
            FormularioTareas,
            ListaTareas
        },
        data() {
            return {
                tareas: []
            };
        },
        methods: {
            agregarTarea(nuevaTarea) {
                this.tareas.push(nuevaTarea);
            },
            eliminarTarea(index) {
                this.tareas.splice(index, 1);
            }
        }
    };
</script>



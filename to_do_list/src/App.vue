<template>
    <div id="app">
        <FormularioTareas @tarea-agregada="agregarTarea" /> 
        <ListaTareas 
                     :tareas="tareas" 
                     @tarea-eliminada="eliminarTarea"  
                     @marcar-completada="marcarCompletada"/>
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
                // Inicializamos el arreglo de tareas como vacío
                tareas: [  ]
            };
        },
        methods: {
            agregarTarea(nuevaTarea) {
                // Al agregar una nueva tarea, la inicializamos con 'completada' en false
                this.tareas.push({ titulo: nuevaTarea, completada: false });
            },
            eliminarTarea(index) {
                this.tareas.splice(index, 1);
            },
            marcarCompletada(index) {
                this.tareas[index].completada = !this.tareas[index].completada;
            }
        }
    };
</script>



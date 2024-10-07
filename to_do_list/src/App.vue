<template>
    <div id="app">
        <MenuHamburguesa @cambiar-filtro="cambiarFiltro" />
        <FormularioTareas @tarea-agregada="agregarTarea" />
        <ListaTareas :tareas="tareasFiltradas"
                     @tarea-eliminada="eliminarTarea"
                     @marcar-completada="marcarCompletada" />
    </div>
</template>

<script>
    import FormularioTareas from './components/FormularioTareas.vue';
    import ListaTareas from './components/ListaTareas.vue';
    import MenuHamburguesa from './components/MenuHamburguesa.vue';


    export default {
        components: {
            FormularioTareas,
            ListaTareas,
            MenuHamburguesa
        },
        data() {
            return {
                // Inicializamos el arreglo de tareas como vacío
                tareas: [],
                filtroActual: 'todas' // Puede ser 'todas', 'completadas' o 'pendientes'
            };
        },
        computed: {
            tareasFiltradas() {
                // Aplica el filtro a las tareas
                if (this.filtroActual === 'pendientes') {
                    return this.tareas.filter(tarea => !tarea.completada);
                } else if (this.filtroActual === 'completadas') {
                    return this.tareas.filter(tarea => tarea.completada);
                }
                else {
                    return this.tareas; // Devuelve todas las tareas si el filtro es 'todas'
                } 
            }
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
            },
            cambiarFiltro(nuevoFiltro) {
                this.filtroActual = nuevoFiltro;
            }
        }
    };
</script>



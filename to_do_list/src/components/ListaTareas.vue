<template>
    <div class="lista-tareas">
        <ul>
            <li v-for="(tarea, index) in tareasFiltradas" :key="index" :class="{ completada: tarea.completada }">
                <span @click="marcarCompletada(index)">
                    {{ tarea.titulo }}
                </span>
                <button @click="eliminarTarea(index)">Eliminar</button>
            </li>
        </ul>
    </div>
</template>

<script>
    export default {
        props: ['tareas', 'filtro'],
        computed: {
            tareasFiltradas() {
                if (this.filtro === 'completadas') {
                    return this.tareas.filter(tarea => tarea.completada);
                } else if (this.filtro === 'pendientes') {
                    return this.tareas.filter(tarea => !tarea.completada);
                } else {
                    return this.tareas;
                }
            }
        },
        methods: {
            eliminarTarea(index) {
                this.$emit('eliminar-tarea', index);
            },
            marcarCompletada(index) {
                this.$emit('marcar-completada', index);
            }
        }
    };
</script>

<template>
    <div class="lista-tareas">
        <ul>
            <li v-for="(tarea, index) in tareas" :key="index" :class="{ completada: tarea.completada }">
                {{ tarea.titulo }}
                <button @click="completarTarea(index)">
                    {{ tarea.completada ? 'Desmarcar' : 'Completar' }}
                </button>
                <button @click="eliminarTarea(index)">Eliminar</button>
            </li>
        </ul>
     </div>
</template>

<script>
    export default {
        props: ['tareas'],
        methods: {
            eliminarTarea(index) {
                this.$emit('tarea-eliminada', index);
            },
            completarTarea(index) {
                this.$emit('marcar-completada', index);
            }
        }
    };
</script>


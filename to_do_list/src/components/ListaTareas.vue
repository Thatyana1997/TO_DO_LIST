<template>
    <div class="lista-tareas">
        <ul>
            <li v-for="(tarea, index) in tareas" :key="index">
                {{ tarea }}
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
            }
        }
    };
</script>

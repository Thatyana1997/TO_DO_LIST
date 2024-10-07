<template>
    <div class="formulario-tareas">
        <input v-model="nuevaTarea" placeholder="Agregar nueva tarea" id="tarea-input" />
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
                const tareaInput = document.getElementById('tarea-input').value.trim();

                if (tareaInput === '') {
                    alert('Por favor, completa el campo de la tarea antes de agregarla.');
                    event.preventDefault(); // Evita que se envíe el formulario
                }
                else {
                    this.$emit('tarea-agregada', this.nuevaTarea);
                    this.nuevaTarea = '';
                }

            }
        }
    };

</script>

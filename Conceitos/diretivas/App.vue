<template>
    <div>
        <h1> Minha lista de tarefas </h1>
        <button @click="() => showList = !showList">
            Ver a lista!
        </button>
        <br />
        <input type="text" v-focus>

        <ul v-if="showList">
            <li
                v-for="(task, index) in tasks"
                :key="`${task}-${index}`"
            >
                {{ tasks.name}}
            </li>
        </ul>
        <p v-else>Lista de tarefas escondidas </p> 
        <!-- Só de ter um v-if acima, o vue detecta que o v-else é relativo ao superior -->
    </div>
</template>

<script>
const focus = { //Hoock, criando uma diretiva
    inserted: (element) => {
        element.focus()
    }
}
export default {
    directives: {
        focus
    },
    data: () => ({
        showList: false,
        tasks: [
            { name: 'Fazer o curso', isDone: false}
        ]
    })
}
</script>

<template>
    <div>
        <h1> Minha lista de tarefas </h1>
        <button @click="handleShowHideList">
            Ver a lista!
        </button>
        <br />
        <input 
            type="text"
            @keyup.enter="addTask"
            v-focus 
            v-model="currentTask">

        <ul v-if="showList">
            <li
                v-for="(task, index) in tasks"
                @dblclick="complete(task)"
                :key="`${task}-${index}`"
                class="task-item"
                :class="{
                    'line-through': task.isDone
                }"
            >
                {{ tasks.name}}
                <button 
                    @click="remove(task)" 
                    
                > &times; </button>
            </li>
        </ul>
        <p v-else>Lista de tarefas escondidas </p> 
         <!-- v-on: == @click -->
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
        currentTask: '',
        showList: false,
        tasks: [
            { name: 'Fazer o curso', isDone: false}
        ]
    }),
    methods: {
        handleShowHideList (){
            this.showList = !this.showList
        },
        addTask() {
            this.tasks.push({
                name: this.currentTask,
                isDone: false
            })
            this.currentTask = ''
        },
        complete (task) {
            this.tasks = this.tasks.map(t => {
                if (t.name === task.name) {
                    return {...t, isDone: !t.isDone}
                }
                return { ...t}
            })
        },
        remove (task) {
            this.tasks = this.tasks.filter(t => t.name !== task.name)
        }
    }
}
</script>

<style scoped>
.line-through {
    text-decoration: line-through;
}
.task-item {
    cursor: pointer;
}
</style>
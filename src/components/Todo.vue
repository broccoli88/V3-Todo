<template>
    <div class="todo">
        <h2>List of Tasks</h2>
        <ul class="list">
            <li v-for="task in tasks" :key="task.id" class="tasks">
                <p>{{ task.task }}</p>
                <button class="remove" @click="removeTask(task.id)">
                    <span><img src="../assets/X.svg" alt="" /></span>
                </button>
            </li>
        </ul>
    </div>
    <div class="add-task">
        <input ref="input" type="text" />
        <button @click="addTask">Add task</button>
    </div>
</template>
d
<script>
export default {
    data() {
        return {
            tasks: [],
            input: "",
        };
    },
    methods: {
        addTask() {
            this.input = this.$refs.input.value;

            if (!this.$refs.input.value) return;
            this.tasks.push({
                task: this.input,
                id: Math.random(),
            });

            this.$refs.input.value = "";
        },

        removeTask(id) {
            this.tasks = this.tasks.filter((task) => task.id !== id);
        },
    },
};
</script>

<style>
.todo {
    margin: 4rem auto;
    width: min(500px, 80vw);
    word-wrap: break-word;
    word-break: break-all;
    background-color: white;
    padding: 1rem;
    border: 1px solid hsl(0, 0%, 0%, 0.2);
    box-shadow: 0 0 10px hsl(0, 0%, 70%, 0.5);
    border-radius: 10px;
}

.list {
    text-align: left;
    list-style: none;
    padding: 0;
    margin-top: 3rem;
}

.tasks {
    border-bottom: 1px solid hsl(0, 0%, 0%, 0.2);
    padding: 0.5rem 0;
    display: flex;
    justify-content: space-between;
    align-items: center;
}

.tasks p {
    margin: 0;
    display: inline;
}

.add-task {
    margin: 0 auto;
    width: min(500px, 80vw);
    padding: 1rem;
}

.add-task input {
    width: 100%;
    padding: 0.6em 0;
    border: 0;
    border-radius: 5px;
    box-shadow: 0 0 10px gray;
}

.buttons {
    display: inline-block;
    align-self: center;
}

.add-task button,
.remove,
.done {
    widows: 10rem;
    border: 0;
    color: white;
    border-radius: 5px;
    cursor: pointer;
}

.add-task button {
    margin-top: 1rem;
    padding: 0.6em 2em;
    background-color: brown;
    box-shadow: 0 0 5px rgb(94, 92, 92);
}

.remove,
.done {
    width: 1.5rem;
    height: 1.5rem;
    background-color: white;
    margin-left: 0.5rem;
}

.remove {
    border: 2px solid crimson;
}

.done {
    border: 2px solid green;
}

.add-task button:active,
.remove:active {
    filter: brightness(120%);
}
</style>
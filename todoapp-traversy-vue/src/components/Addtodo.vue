<template>
    <div>
        <form @submit="addTodo">
            <input type="text" v-model="title" name="title" placeholder="Add To-Do"/>
            <input type="submit" class="btn" />
        </form>
    </div>
</template>

<script>
// import uuid from 'uuid';

export default {
    name: "Addtodo",
    data() {
        return {
            title: ''
        }
    },
    methods: {
        addTodo(e) {
            e.preventDefault();
            const newTodo = {
                // id: uuid.v4() dont need this bc json data will give id,
                title: this.title,
                completed: false
            }
            this.$emit('add-todo', newTodo)

            this.title = '';
        }
    }
}
</script>

<style scoped>
    form {
        display: flex;
    }

    input[type="text"] {
        flex: 10;
        padding: 5px;
    }

    input[type="submit"] {
        flex: 2
    }
</style>
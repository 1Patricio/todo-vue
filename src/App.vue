<template>
    <div class="px-3 py-10 md:px-10">
        <div class="w-full sm:w-1/2 lg:w-1/3 mx-auto">

            <pre class="from-neutral-50">
            {{ $store.state.todos }}
            </pre>

            <TodoSpinner />
            <TodoFormAdd />
            <TodoItems />
            <TodoEmpty />
        </div>
    </div>

</template>

<script>
import axios from 'axios';
import TodoEmpty from './components/TodoEmpty.vue';
import TodoFormAdd from './components/TodoFormAdd.vue';
import TodoItems from './components/TodoItems.vue';
import TodoSpinner from './components/TodoSpinner.vue';


export default {
    name: 'App',
    components: {
        TodoSpinner,
        TodoFormAdd,
        TodoItems,
        TodoEmpty
    },
    created() {
        axios.get('http://localhost:3000/todos')
            .then((response) => {
                this.$store.commit('storeTodos', response.data)
            })
    },
}
</script>
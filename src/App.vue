<template>
    <div class="px-3 py-10 md:px-10">
        <div class="w-full sm:w-1/2 lg:w-1/3 mx-auto">

            <pre class="from-neutral-50">
            </pre>

            <TodoSpinner v-if="loading"/>
            <div v-else>
                <TodoFormAdd />
                <TodoItems />
                <TodoEmpty />
            </div>
        </div>
    </div>

</template>

<script>
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
    data() {
        return {
            loading: false
        }
    },
    created() {
        this.loading = true
        this.$store.dispatch('getTodos').then(() => {
            this.loading = false
        })
    },
}
</script>
<template>
    <div class="flex min-h-screen">
        <div
            class="flex-1 flex items-center justify-center px-3 py-10 md:px-10"
        >
            <div class="w-full sm:w-1/2 lg:w-2/3 mx-auto">
                <TodoSpinner v-if="loading" />
                <div v-else>
                    <TodoFormAdd />
                    <TodoItems v-if="$store.state.todos.length" />
                    <TodoEmpty v-else />
                </div>
            </div>
        </div>
        <div
            class="hidden md:flex flex-col items-center justify-center px-10 py-10"
        >
            <TodoStateImage />
        </div>
    </div>
</template>

<script>
import { ref } from 'vue'
import { useStore } from 'vuex'
import TodoEmpty from './components/TodoEmpty.vue'
import TodoFormAdd from './components/TodoFormAdd.vue'
import TodoItems from './components/TodoItems.vue'
import TodoSpinner from './components/TodoSpinner.vue'
import TodoStateImage from './components/TodoStateImage.vue'

export default {
    name: 'App',
    components: {
        TodoSpinner,
        TodoFormAdd,
        TodoItems,
        TodoEmpty,
        TodoStateImage
    },

    setup() {
        const loading = ref(false);
        const store = useStore()

        loading.value = true
        store.dispatch('getTodos').finally(() => {
            loading.value = false
        })

        return{
            loading
        }
    },

    created() {

    }
}
</script>

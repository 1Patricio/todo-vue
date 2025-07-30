<template>
    <div
        class="flex flex-col items-center justify-center"
        v-if="$store.state.todos.filter((todo) => !todo.completed).length <= 3"
    >
        <img src="@/assets/img/1.png" alt="" class="h-80 w-80" />
        <span class="text-lg text-gray-100">Tudo sob controle</span>
    </div>

    <div
        class="flex flex-col items-center justify-center"
        v-if="
            $store.state.todos.filter((todo) => !todo.completed).length > 3 &&
            $store.state.todos.filter((todo) => !todo.completed).length <= 6
        "
    >
        <img src="@/assets/img/2.png" alt="" class="h-80 w-80" />
        <span class="text-lg text-gray-100">Muitos afazeres</span>

    </div>

    <div
        class="flex flex-col items-center justify-center"
        v-if="
            $store.state.todos.filter((todo) => !todo.completed).length > 6
        "
    >
        <img src="@/assets/img/3.png" alt="" class="h-80 w-80" />
        <span class="text-lg text-gray-100">Hora de colocar a casa em ordem!</span>

    </div>

    <span v-if="$store.state.todos && !$store.state.loading" class="text-white">
        Total de tarefas pendentes:
        {{ $store.state.todos.filter((todo) => !todo.completed).length }}
    </span>
</template>

<script>
export default {}
</script>
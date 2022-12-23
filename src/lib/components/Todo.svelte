<script>
    import {createEventDispatcher} from 'svelte';
    import {fly} from 'svelte/transition';

    export let todo;

    let flyInParameters = {
        y: 100,
        duration: 1000
    }

    let flyOutParameters = {
        x: 350,
        duration: 600
    }

    const dispatch = createEventDispatcher();
    function toggleTodoStatus(id) {
        dispatch('todoUpdated', {
            id: id
        })
    }

    function deleteTodo() {
        dispatch('todoDeleted', {
            todo: todo
        });
    }
</script>
<li class="todo-list list-item-view" class:completed="{todo.completed}" in:fly={flyInParameters} out:fly={flyOutParameters}>
    <span>
    <button class="btn btn-done fa-solid fa-square 
    { todo.completed ? 'fa-square-check': 'fa-square' }"
    on:click = {() => toggleTodoStatus(todo.id)}
    ></button>
    <span>{ todo.text }</span>
    </span>
    <button class="btn btn-delete fa-solid fa-trash" on:click={deleteTodo}></button>
</li>

<style>
.todo-list:first-of-type {
    border-top: 1px solid rgb(121, 121, 121);
    padding-top: 10px;
}

.list-item-view {
    padding-top: 5px;
    padding-bottom: 0px;
    display: flex;
    align-items: center;
    justify-content: space-between;
}

.completed {
    color: #6a6f75;
    opacity: 0.5;
}
</style>
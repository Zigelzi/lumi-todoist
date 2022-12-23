<script>
    import { createEventDispatcher } from "svelte";
    const dispatch = createEventDispatcher();
    let newTodoText;

    function addTodo(event) {
        if (event.type === 'click' || event.code === 'Enter') {
            dispatch('todoAdded', {
            text: newTodoText
        });
        
        newTodoText = '';
        }
    }
</script>
<!-- Add form at bottom -->
<div class="app-form">
    <input placeholder="Add Todo.." type="text" class="input-text" name="" bind:value={newTodoText} on:keyup={addTodo}>
    <button class="btn fa-solid fa-plus" on:click={addTodo}></button>
</div>

<style>
.app-form {
    margin-bottom: 10px;
    display: flex;
    justify-content: center;
}

.input-text {
    height: 40px;
    background: #282c34;
    font-size: 15px;
    border: 1px solid #a2a8ad;
    color: #dce4ec;
    width: 100%;
    margin-right: 15px;
    border-radius: 2em;
    padding: 5px 10px;
    transition: border 250ms ease-out;
}

.input-text:focus {
    border: 1px solid #ffffff;
    background: #1d2025;
    outline: none;
    color: #dce4ec;
}

    ::placeholder {
    opacity: 0.3;
}
</style>
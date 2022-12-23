<script>
    import Header from '$lib/components/Header.svelte';
    import Form from '$lib/components/Form.svelte';
    import TodoList from '$lib/components/TodoList.svelte';

    let todos = [
        { id: 1, text :'Do dishes', completed: false },
        { id: 2, text :'Read emails', completed: true },
        { id: 3, text :'Wash clothes', completed: false },
    ]


    let totalTodos;
    let remainingTodos;

    $: totalTodos = todos.length;
    $: remainingTodos = countRemainingTodos(todos);

    function updateTodo(event) {
        let updatedTodoId = event.detail.id;
        let todo = todos.find(todo => todo.id === updatedTodoId)
        todo.completed = !todo.completed;
        todos = todos;
    }

    function countRemainingTodos(todos) {
        let unfinishedTodos = 0;
        todos.forEach(todo => {
            if(!todo.completed) {
                unfinishedTodos++;
            }
        });
        return unfinishedTodos;
    }

    function addNewTodo(event) {
        let newTodoText = event.detail.text.trim();

        if (newTodoText !== "") {
            let currentMaxIndex = todos.reduce((previous, todo) => Math.max(previous, todo.id), 0);
            let newId = currentMaxIndex + 1;
            let newTodo = {
                id: newId,
                text: newTodoText,
                completed: false
            }

            todos.push(newTodo);
            todos = todos;
        }
    }

    function deleteTodoFromList(event) {
        let todoIndex = todos.indexOf(event.detail.todo)
        if (todoIndex > -1) {
            todos.splice(todoIndex, 1)
        }
        todos = todos;
    }
</script>

<div id="app-container" class="app-container">
    <Header {totalTodos} {remainingTodos}/>
    <TodoList todos = { todos } on:todoUpdated={updateTodo} on:todoDeleted={deleteTodoFromList}/>
    <Form on:todoAdded={addNewTodo}/>
</div>

<style>
.app-container {
    width: 400px;
    min-height: 500px;
    background-color: #282c34;
    box-shadow: 0 20px 80px rgba(0, 0, 0, 0.6);
    background: radial-gradient(circle, #282c34 0%, rgba(40, 48, 56, 1) 100%);
    position: relative;
    border-radius: 1em;
    padding: 20px;
    display: flex;
    flex-direction: column;
    justify-content: space-between;
}
</style>
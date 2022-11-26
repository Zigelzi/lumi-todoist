<script>
    import Header from '$lib/components/Header.svelte';
    import Form from '$lib/components/Form.svelte';
    import TodoList from '$lib/components/TodoList.svelte';
</script>

<div id="app-container" class="app-container">
    <Header/>
    <TodoList />
    <Form />
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
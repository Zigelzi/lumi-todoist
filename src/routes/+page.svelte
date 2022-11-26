<div id="app-container" class="app-container">

    <!-- Header with information -->
    <div class="app-header">
        <div>10 Total</div>
        <div class="task-count">1 Remaining</div>
    </div>

    <!-- List of actual todos -->
    <div class="app-body">
        <ul>

            <li class="todo-list list-item-view">
                <span>
        <button class="btn btn-done fa-solid fa-square"></button>
        <span>First Todo</span>
                </span>
                <button class="btn btn-delete fa-solid fa-trash"></button>
            </li>

            <li class="todo-list list-item-view completed">
                <!-- <div class="list-item-view"> -->
                <span>
        <button class="btn btn-done"><i class="fa-solid fa-check-square"></i></button>
        <span>First Todo</span>
                </span>
                <button class="btn btn-delete fa-solid fa-trash"></button>
                <!-- </div> -->
            </li>


        </ul>
    </div>

    <!-- Add form at bottom -->
    <div class="app-form">
        <input placeholder="Add Todo.." type="text" class="input-text" name="">
        <button class="btn fa-solid fa-plus"></button>
    </div>

</div>
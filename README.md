<!DOCTYPE html>
<html lang="en">

<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Simple To-Do List</title>
    <style>
        body {
            font-family: Arial, sans-serif;
            margin: 20px;
        }

        #completedTasks {
            margin-top: 20px;
        }

        .completed {
            text-decoration: line-through;
            color: blue;
        }
    </style>
</head>

<body>
    <h1>Simple To-Do List</h1>
    <input type="text" id="taskInput" placeholder="Add a new task">
    <button onclick="addTask()">Add Task</button>

    <h2>Tasks</h2>
    <ul id="taskList"></ul>

    <h2>Completed Tasks</h2>
    <ol id="completedTasks"></ol>

    <script>
        const tasks = [];

        function addTask() {
            const taskInput = document.getElementById('taskInput');
            const task = taskInput.value.trim();
            if (task) {
                tasks.push({ name: task, completed: false });
                taskInput.value = '';
                renderTasks();
            }
        }

        function toggleComplete(index) {
            tasks[index].completed = !tasks[index].completed;
            renderTasks();
        }

        function renderTasks() {
            const taskList = document.getElementById('taskList');
            const completedTasks = document.getElementById('completedTasks');

            taskList.innerHTML = '';
            completedTasks.innerHTML = '';

            tasks.forEach((task, index) => {
                const li = document.createElement('li');
                li.textContent = task.name;
                li.className = task.completed ? 'completed' : '';
                li.onclick = () => toggleComplete(index);
                taskList.appendChild(li);
            });

            tasks.forEach((task, index) => {
                if (task.completed) {
                    const li = document.createElement('li');
                    li.textContent = task.name;
                    completedTasks.appendChild(li);
                }
            });
        }
    </script>
</body>

</html>

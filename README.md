<!DOCTYPE html>
<html lang="pt-br">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0"/>
  <title>Lista de Tarefas</title>
  <style>
    body {
      font-family: Arial, sans-serif;
      background: #f0f0f5;
      display: flex;
      justify-content: center;
      align-items: center;
      height: 100vh;
      margin: 0;
    }

    .todo-container {
      background: #ffffff;
      padding: 30px;
      border-radius: 12px;
      box-shadow: 0 4px 12px rgba(0, 0, 0, 0.1);
      width: 100%;
      max-width: 400px;
    }

    h1 {
      text-align: center;
      color: #333;
    }

    .input-group {
      display: flex;
      margin-bottom: 20px;
    }

    input[type="text"] {
      flex: 1;
      padding: 10px;
      border: 1px solid #ccc;
      border-radius: 8px 0 0 8px;
    }

    button {
      padding: 10px 15px;
      border: none;
      background: #4caf50;
      color: white;
      border-radius: 0 8px 8px 0;
      cursor: pointer;
      transition: 0.3s;
    }

    button:hover {
      background: #45a049;
    }

    ul {
      list-style-type: none;
      padding: 0;
    }

    li {
      background: #f8f8f8;
      padding: 10px;
      border-radius: 6px;
      margin-bottom: 10px;
      display: flex;
      justify-content: space-between;
      align-items: center;
      transition: 0.3s;
    }

    li.completed {
      text-decoration: line-through;
      color: #555454;
    }

    .delete-btn {
      background: #f33a25;
      border: none;
      color: white;
      padding: 6px 10px;
      border-radius: 6px;
      cursor: pointer;
    }

    .delete-btn:hover {
      background: #f33a25;
    }
  </style>
</head>
<body>
  <div class="todo-container">
    <h1>Lista de Tarefas</h1>
    <div class="input-group">
      <input type="text" id="taskInput" placeholder="Digite uma tarefa" />
      <button onclick="addTask()">Adicionar</button>
    </div>
    <ul id="taskList"></ul>
  </div>

  <script>
    function addTask() {
      const taskInput = document.getElementById("taskInput");
      const taskText = taskInput.value.trim();

      if (taskText === "") return;

      const li = document.createElement("li");
      li.innerHTML = `
        <span onclick="toggleTask(this)">${taskText}</span>
        <button class="delete-btn" onclick="deleteTask(this)">Excluir</button>
      `;

      document.getElementById("taskList").appendChild(li);
      taskInput.value = "";
    }

    function toggleTask(element) {
      element.parentElement.classList.toggle("completed");
    }

    function deleteTask(button) {
      button.parentElement.remove();
    }
  </script>
</body>
</html>
# Ex03 To-Do List using JavaScript
## Date:

## AIM
To create a To-do Application with all features using JavaScript.

## ALGORITHM
### STEP 1
Build the HTML structure (index.html).

### STEP 2
Style the App (style.css).

### STEP 3
Plan the features the To-Do App should have.

### STEP 4
Create a To-do application using Javascript.

### STEP 5
Add functionalities.

### STEP 6
Test the App.

### STEP 7
Open the HTML file in a browser to check layout and functionality.

### STEP 8
Fix styling issues and refine content placement.

### STEP 9
Deploy the website.

### STEP 10
Upload to GitHub Pages for free hosting.

## PROGRAM
```
<html>
<head>
  <title>Todo App</title>
  <link rel="stylesheet" href="style.css">
</head>
<body>
  <div class="container">
    <input type="text" id="task-input" placeholder="Add a new task...">
    <button id="add-btn">Add</button>
    <div id="task-list"></div>
  </div>
  <script src="script.js"></script>
</body>
</html>

# Style.css
body {
  font-family: 'Arial', sans-serif;
  background: linear-gradient(135deg, #f06, #4a90e2);
  display: flex;
  justify-content: center;
  align-items: center;
  height: 100vh;
  margin: 0;
  color: #fff;
}
.container {
  background: rgba(255,255,255,0.1);
  padding: 2rem;
  border-radius: 15px;
  box-shadow: 0 10px 30px rgba(0,0,0,0.2);
  width: 100%;
  max-width: 400px;
}
input[type="text"], button {
  padding: 0.8rem;
  border-radius: 8px;
  border: none;
  outline: none;
  font-size: 1rem;
  margin-right: 1rem;
}
button {
  background: #ff6b6b;
  color: #fff;
  cursor: pointer;
  transition: background 0.3s;
}
button:hover {
  background: #ff4757;
}
.todo {
  background: rgba(255,255,255,0.2);
  border-radius: 8px;
  margin-top: 1rem;
  display: flex;
  justify-content: space-between;
  align-items: center;
  padding: 0.8rem;
  box-shadow: 0 5px 15px rgba(0,0,0,0.1);
  transition: transform 0.2s, background 0.3s;
}
.todo:hover {
  transform: translateY(-3px);
  background: rgba(255,255,255,0.3);
}
.task {
  flex: 1;
  font-size: 1rem;
  cursor: pointer;
}
.delete, .edit {
  cursor: pointer;
  transition: transform 0.2s, color 0.3s;
}
.delete:hover {
  transform: scale(1.1);
  color: #ff4757;
}
.edit:hover {
  transform: scale(1.1);
  color: #1e90ff;
}

# Script.js
let input = document.getElementById('task-input');
let btn = document.getElementById('add-btn');
let taskList = document.getElementById('task-list');
let tasks = [];

let localData = localStorage.getItem("taskArray");
if (localData) {
  tasks = JSON.parse(localData);
  renderTasks();
}

btn.addEventListener("click", function() {
  let value = input.value.trim();
  if (!value) {
    alert("Please enter a task.");
    return;
  }
  let taskObj = { id: Date.now(), text: value };
  tasks.push(taskObj);
  localStorage.setItem("taskArray", JSON.stringify(tasks));
  input.value = "";
  renderTasks();
});

function renderTasks() {
  taskList.innerHTML = "";
  tasks.forEach(task => {
    let element = document.createElement('div');
    element.className = 'todo';
    element.innerHTML = `
      <span class="task" contenteditable="false">${task.text}</span>
      <button class='edit'>Edit</button>
      <span class="delete">&#10006;</span>
    `;
    // Delete Task
    element.querySelector('.delete').onclick = function() {
      tasks = tasks.filter(t => t.id !== task.id);
      localStorage.setItem("taskArray", JSON.stringify(tasks));
      renderTasks();
    };
    // Edit Task
    let taskText = element.querySelector('.task');
    let editBtn = element.querySelector('.edit');
    editBtn.onclick = function() {
      if (editBtn.textContent === 'Edit') {
        taskText.setAttribute('contenteditable', 'true');
        taskText.focus();
        editBtn.textContent = 'Save';
      } else {
        let updatedText = taskText.textContent.trim();
        if (updatedText) {
          task.text = updatedText;
          localStorage.setItem("taskArray", JSON.stringify(tasks));
        }
        taskText.setAttribute('contenteditable', 'false');
        editBtn.textContent = 'Edit';
      }
    };
    taskList.appendChild(element);
  });
}

```

## OUTPUT
<img width="1910" height="868" alt="image" src="https://github.com/user-attachments/assets/0f16cc6e-bc6b-420d-8e53-81bbaeb23986" />
<img width="1909" height="953" alt="image" src="https://github.com/user-attachments/assets/6dc32699-4561-492b-bdce-c9bc2ad41ecf" />

## RESULT
The program for creating To-do list using JavaScript is executed successfully.

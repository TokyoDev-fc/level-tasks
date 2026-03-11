const taskInput = document.getElementById("taskInput");
const addTaskBtn = document.getElementById("addTaskBtn");
const taskList = document.getElementById("taskList");
const taskCount = document.getElementById("taskCount");

const xpText = document.getElementById("xp");
const levelText = document.getElementById("level");
const nextLevelXpText = document.getElementById("nextLevelXp");
const progressBar = document.getElementById("progressBar");
const progressPercent = document.getElementById("progressPercent");

let xp = 0;
let level = 1;
let nextLevelXp = 100;

function updateStatus() {
  xpText.textContent = xp;
  levelText.textContent = level;
  nextLevelXpText.textContent = `${nextLevelXp} XP`;

  let progress = (xp / nextLevelXp) * 100;

  if (progress > 100) {
    progress = 100;
  }

  progressBar.style.width = `${progress}%`;
  progressPercent.textContent = `${Math.round(progress)}%`;
}

function updateTaskCount() {
  const total = document.querySelectorAll(".task-item").length;
  taskCount.textContent = total;

  if (total === 0) {
    taskList.innerHTML = `<p class="empty-message">Nenhuma missão criada ainda.</p>`;
  } else {
    const emptyMessage = taskList.querySelector(".empty-message");
    if (emptyMessage) {
      emptyMessage.remove();
    }
  }
}

function checkLevelUp() {
  while (xp >= nextLevelXp) {
    xp -= nextLevelXp;
    level++;
    nextLevelXp += 50;
    alert(`Parabéns! Você subiu para o nível ${level}!`);
  }

  updateStatus();
}

function createTask() {
  const text = taskInput.value.trim();

  if (text === "") {
    alert("Digite uma missão antes de adicionar.");
    return;
  }

  const emptyMessage = taskList.querySelector(".empty-message");
  if (emptyMessage) {
    emptyMessage.remove();
  }

  const taskXp = 20;

  const li = document.createElement("li");
  li.classList.add("task-item");

  const taskLeft = document.createElement("div");
  taskLeft.classList.add("task-left");

  const taskMark = document.createElement("span");
  taskMark.classList.add("task-mark");

  const taskContent = document.createElement("div");
  taskContent.classList.add("task-content");

  const span = document.createElement("span");
  span.classList.add("task-text");
  span.textContent = text;

  const xpBadge = document.createElement("span");
  xpBadge.classList.add("task-xp");
  xpBadge.textContent = `+${taskXp} XP`;

  taskContent.appendChild(span);
  taskContent.appendChild(xpBadge);

  taskLeft.appendChild(taskMark);
  taskLeft.appendChild(taskContent);

  const taskActions = document.createElement("div");
  taskActions.classList.add("task-actions");

  const completeBtn = document.createElement("button");
  completeBtn.classList.add("complete-btn");
  completeBtn.textContent = "Concluir";

  const deleteBtn = document.createElement("button");
  deleteBtn.classList.add("delete-btn");
  deleteBtn.textContent = "Excluir";

  let completed = false;

  completeBtn.addEventListener("click", function () {
    if (!completed) {
      span.classList.add("done");
      xp += taskXp;
      completed = true;
      completeBtn.textContent = "Concluída";
      completeBtn.disabled = true;
      checkLevelUp();
    }
  });

  deleteBtn.addEventListener("click", function () {
    li.remove();
    updateTaskCount();
  });

  taskActions.appendChild(completeBtn);
  taskActions.appendChild(deleteBtn);

  li.appendChild(taskLeft);
  li.appendChild(taskActions);

  taskList.appendChild(li);

  taskInput.value = "";
  taskInput.focus();

  updateTaskCount();
}

addTaskBtn.addEventListener("click", createTask);

taskInput.addEventListener("keydown", function (event) {
  if (event.key === "Enter") {
    createTask();
  }
});

updateStatus();
updateTaskCount();

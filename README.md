# Ex03 To-Do List using JavaScript
## Date : 17/11/2026
## Register No : 212225040153
## Name : JESSIE J

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

index.html
```

<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>My To-Do Planner</title>
    <link rel="stylesheet" href="style.css">
</head>
<body>

<div class="app">

    <!-- Sidebar -->
    <aside class="sidebar">
        <div class="logo">
            <span>♡</span> Daily Planner
        </div>

        <div class="profile">
            <div class="profile-icon">J</div>
            <div>
                <h3>My Planner</h3>
                <p>Stay productive!</p>
            </div>
        </div>

        <nav>
            <p class="nav-heading">MENU</p>

            <button class="nav-btn active" data-filter="all">
                <span>▣</span> All Tasks
                <span class="nav-count" id="allCount">0</span>
            </button>

            <button class="nav-btn" data-filter="pending">
                <span>◷</span> Pending
                <span class="nav-count" id="pendingCount">0</span>
            </button>

            <button class="nav-btn" data-filter="completed">
                <span>✓</span> Completed
                <span class="nav-count" id="completedCount">0</span>
            </button>

            <p class="nav-heading">CATEGORIES</p>

            <button class="nav-btn category-btn" data-category="College">
                <span>🎓</span> College
            </button>

            <button class="nav-btn category-btn" data-category="Personal">
                <span>♡</span> Personal
            </button>

            <button class="nav-btn category-btn" data-category="Work">
                <span>💼</span> Work
            </button>

            <button class="nav-btn category-btn" data-category="Other">
                <span>✦</span> Others
            </button>
        </nav>

        <div class="sidebar-bottom">
            <button id="themeToggle" class="theme-toggle">
                <span id="themeIcon">☾</span>
                <span id="themeText">Dark Mode</span>
            </button>
            <p>Made with ♡</p>
        </div>
    </aside>


    <!-- Main Content -->
    <main class="main-content">

        <header>
            <div>
                <p class="welcome">HELLO, WELCOME BACK ♡</p>
                <h1>My To-Do List</h1>
                <p class="subtitle" id="todayDate"></p>
            </div>

            <div class="header-right">
                <div class="date-box">
                    <span>📅</span>
                    <div>
                        <small>Today's Date</small>
                        <p id="headerDate"></p>
                    </div>
                </div>
            </div>
        </header>


        <!-- Statistics -->
        <section class="stats">

            <div class="stat-card">
                <div class="stat-icon burgundy-icon">▣</div>
                <div>
                    <p>Total Tasks</p>
                    <h2 id="totalTasks">0</h2>
                </div>
            </div>

            <div class="stat-card">
                <div class="stat-icon green-icon">✓</div>
                <div>
                    <p>Completed</p>
                    <h2 id="completedTasks">0</h2>
                </div>
            </div>

            <div class="stat-card">
                <div class="stat-icon yellow-icon">◷</div>
                <div>
                    <p>Pending</p>
                    <h2 id="pendingTasks">0</h2>
                </div>
            </div>

            <div class="stat-card">
                <div class="stat-icon red-icon">⚑</div>
                <div>
                    <p>Overdue</p>
                    <h2 id="overdueTasks">0</h2>
                </div>
            </div>

        </section>


        <!-- Progress -->
        <section class="progress-container">
            <div class="progress-info">
                <div>
                    <h3>Daily Progress</h3>
                    <p>Keep going! You're doing great.</p>
                </div>
                <h2 id="progressPercent">0%</h2>
            </div>

            <div class="progress-bar">
                <div id="progressBar"></div>
            </div>
        </section>


        <!-- Add Task -->
        <section class="add-task-section">
            <div class="section-heading">
                <div>
                    <h2>Add a New Task</h2>
                    <p>Plan your day and stay organized.</p>
                </div>
                <span class="heading-heart">♡</span>
            </div>

            <form id="taskForm">

                <input type="hidden" id="editId">

                <div class="form-grid">

                    <div class="form-group task-name">
                        <label for="taskInput">Task Name</label>
                        <input type="text" id="taskInput"
                            placeholder="What do you need to do?" required>
                    </div>

                    <div class="form-group">
                        <label for="category">Category</label>
                        <select id="category">
                            <option value="College">College</option>
                            <option value="Personal">Personal</option>
                            <option value="Work">Work</option>
                            <option value="Other">Other</option>
                        </select>
                    </div>

                    <div class="form-group">
                        <label for="priority">Priority</label>
                        <select id="priority">
                            <option value="High">High</option>
                            <option value="Medium" selected>Medium</option>
                            <option value="Low">Low</option>
                        </select>
                    </div>

                    <div class="form-group">
                        <label for="dueDate">Due Date</label>
                        <input type="date" id="dueDate">
                    </div>

                </div>

                <div class="form-actions">
                    <button type="submit" class="add-btn" id="submitBtn">
                        + Add Task
                    </button>
                    <button type="reset" class="reset-btn" id="resetBtn">
                        Clear
                    </button>
                </div>

            </form>
        </section>


        <!-- Search and Filter -->
        <section class="task-toolbar">

            <div class="search-box">
                <span>⌕</span>
                <input type="search" id="searchInput"
                    placeholder="Search your tasks...">
            </div>

            <select id="sortFilter" class="toolbar-select">
                <option value="newest">Newest First</option>
                <option value="oldest">Oldest First</option>
                <option value="priority">Priority</option>
                <option value="date">Due Date</option>
            </select>

            <button id="clearAllBtn" class="clear-btn">
                Clear All
            </button>

        </section>


        <!-- Task List -->
        <section class="task-section">

            <div class="section-heading">
                <div>
                    <h2 id="listTitle">Today's Tasks</h2>
                    <p id="taskSubtitle">Manage your daily activities.</p>
                </div>

                <span class="task-count" id="taskCount">0 Tasks</span>
            </div>

            <div id="taskList" class="task-list">

                <div class="empty">
                    <div>♡</div>
                    <h3>No tasks yet!</h3>
                    <p>Add your first task and start organizing your day.</p>
                </div>

            </div>

        </section>


        <!-- Calendar -->
        <section class="calendar-section">

            <div class="section-heading">
                <div>
                    <h2>My Calendar</h2>
                    <p>Keep track of your important dates.</p>
                </div>
            </div>

            <div class="calendar">

                <div class="calendar-header">
                    <button id="prevMonth">❮</button>
                    <h3 id="monthYear"></h3>
                    <button id="nextMonth">❯</button>
                </div>

                <div class="calendar-grid" id="calendarGrid"></div>

                <p class="calendar-note">
                    <span></span> Days with tasks are marked with a dot.
                </p>

            </div>

        </section>


        <footer>
            <p>Organize your day, achieve your goals. ♡</p>
            <p>Made with love | Daily Planner</p>
        </footer>

    </main>

</div>

<script src="script.js"></script>
</body>
</html>

```

style.css

```

/* GENERAL */

* {
    margin: 0;
    padding: 0;
    box-sizing: border-box;
}

:root {
    --primary: #702D3D;
    --secondary: #A66B78;
    --background: #F8F3EB;
    --card: #FFFCF7;
    --text: #4A3030;
    --muted: #89766F;
    --border: #E8D8C3;
    --soft: #F1E7DA;
    --green: #557A60;
    --red: #A34D55;
    --yellow: #A17A36;
    --shadow: 0 5px 20px rgba(80, 40, 40, 0.06);
}

body {
    font-family: 'Segoe UI', Arial, sans-serif;
    background: var(--background);
    color: var(--text);
    min-height: 100vh;
    transition: 0.3s;
}

body.dark {
    --primary: #D18B9B;
    --secondary: #A66B78;
    --background: #21191B;
    --card: #302326;
    --text: #F8F0E8;
    --muted: #C2AAA5;
    --border: #594047;
    --soft: #49333A;
    --green: #91B99A;
    --red: #E49A9F;
    --yellow: #E3C17D;
    --shadow: 0 5px 20px rgba(0, 0, 0, 0.15);
}

/* MAIN LAYOUT */

.app {
    display: flex;
    min-height: 100vh;
}

/* SIDEBAR */

.sidebar {
    width: 255px;
    min-width: 255px;
    background: var(--primary);
    color: #fff;
    padding: 30px 20px;
    display: flex;
    flex-direction: column;
    min-height: 100vh;
}

.logo {
    font-size: 22px;
    font-weight: bold;
    margin-bottom: 35px;
}

.logo span {
    font-size: 27px;
    margin-right: 7px;
}

.profile {
    display: flex;
    align-items: center;
    gap: 12px;
    padding: 15px 10px;
    background: rgba(255,255,255,0.12);
    border-radius: 12px;
    margin-bottom: 30px;
}

.profile-icon {
    width: 42px;
    height: 42px;
    border-radius: 50%;
    background: #E8D8C3;
    color: #702D3D;
    display: grid;
    place-items: center;
    font-size: 20px;
    font-weight: bold;
}

.profile h3 {
    font-size: 14px;
}

.profile p {
    font-size: 12px;
    opacity: 0.75;
    margin-top: 4px;
}

.nav-heading {
    font-size: 11px;
    letter-spacing: 1.5px;
    opacity: 0.65;
    margin: 20px 10px 10px;
}

.nav-btn {
    width: 100%;
    display: flex;
    align-items: center;
    gap: 12px;
    padding: 13px 12px;
    margin-bottom: 6px;
    background: transparent;
    color: #fff;
    border: none;
    border-radius: 9px;
    cursor: pointer;
    text-align: left;
    font-size: 14px;
    transition: 0.3s;
}

.nav-btn:hover,
.nav-btn.active {
    background: rgba(255,255,255,0.17);
}

.nav-btn span:first-child {
    font-size: 18px;
}

.nav-count {
    margin-left: auto;
    background: rgba(255,255,255,0.2);
    padding: 3px 8px;
    border-radius: 15px;
    font-size: 11px;
}

.sidebar-bottom {
    margin-top: auto;
    text-align: center;
    padding-top: 30px;
}

.theme-toggle {
    width: 100%;
    padding: 13px;
    background: rgba(255,255,255,0.13);
    border: none;
    border-radius: 9px;
    color: white;
    cursor: pointer;
    margin-bottom: 18px;
    font-size: 14px;
}

.sidebar-bottom p {
    font-size: 12px;
    opacity: 0.7;
}

/* MAIN CONTENT */

.main-content {
    flex: 1;
    padding: 35px;
    max-width: 1500px;
    margin: auto;
    min-width: 0;
}

header {
    display: flex;
    justify-content: space-between;
    align-items: center;
    margin-bottom: 30px;
}

.welcome {
    font-size: 11px;
    letter-spacing: 2px;
    color: var(--secondary);
    font-weight: bold;
    margin-bottom: 8px;
}

header h1 {
    font-size: 34px;
    color: var(--primary);
}

.subtitle {
    color: var(--muted);
    margin-top: 7px;
    font-size: 14px;
}

.header-right {
    display: flex;
    gap: 10px;
}

.date-box {
    display: flex;
    gap: 12px;
    align-items: center;
    background: var(--card);
    border: 1px solid var(--border);
    border-radius: 12px;
    padding: 12px 18px;
}

.date-box span {
    font-size: 25px;
}

.date-box small {
    color: var(--muted);
}

.date-box p {
    font-weight: bold;
    margin-top: 4px;
}

/* STATISTICS */

.stats {
    display: grid;
    grid-template-columns: repeat(4, 1fr);
    gap: 16px;
    margin-bottom: 22px;
}

.stat-card {
    display: flex;
    align-items: center;
    gap: 15px;
    background: var(--card);
    padding: 20px;
    border-radius: 14px;
    border: 1px solid var(--border);
    box-shadow: var(--shadow);
}

.stat-icon {
    width: 48px;
    height: 48px;
    display: grid;
    place-items: center;
    font-size: 24px;
    border-radius: 12px;
}

.burgundy-icon {
    background: #F0DEE2;
    color: #702D3D;
}

.green-icon {
    background: #E0EBDD;
    color: #557A60;
}

.yellow-icon {
    background: #F5EBD2;
    color: #A17A36;
}

.red-icon {
    background: #F4DDDD;
    color: #A34D55;
}

.stat-card p {
    color: var(--muted);
    font-size: 13px;
}

.stat-card h2 {
    font-size: 25px;
    margin-top: 5px;
    color: var(--primary);
}

/* PROGRESS */

.progress-container {
    background: var(--card);
    padding: 23px;
    border: 1px solid var(--border);
    border-radius: 14px;
    box-shadow: var(--shadow);
    margin-bottom: 25px;
}

.progress-info {
    display: flex;
    justify-content: space-between;
    align-items: center;
    margin-bottom: 15px;
}

.progress-info h3 {
    font-size: 17px;
}

.progress-info p {
    color: var(--muted);
    font-size: 13px;
    margin-top: 5px;
}

.progress-info h2 {
    color: var(--primary);
}

.progress-bar {
    width: 100%;
    height: 11px;
    background: var(--soft);
    border-radius: 20px;
    overflow: hidden;
}

#progressBar {
    height: 100%;
    width: 0%;
    background: linear-gradient(90deg, var(--primary), var(--secondary));
    border-radius: 20px;
    transition: 0.4s;
}

/* ADD TASK */

.add-task-section {
    background: var(--card);
    padding: 24px;
    border-radius: 14px;
    border: 1px solid var(--border);
    box-shadow: var(--shadow);
    margin-bottom: 25px;
}

.section-heading {
    display: flex;
    justify-content: space-between;
    align-items: center;
    margin-bottom: 20px;
}

.section-heading h2 {
    font-size: 19px;
    color: var(--text);
}

.section-heading p {
    font-size: 13px;
    color: var(--muted);
    margin-top: 5px;
}

.heading-heart {
    font-size: 30px;
    color: var(--secondary);
}

.form-grid {
    display: grid;
    grid-template-columns: 2fr 1fr 1fr 1fr;
    gap: 14px;
}

.form-group {
    display: flex;
    flex-direction: column;
    gap: 8px;
}

.form-group label {
    font-size: 13px;
    font-weight: 600;
}

.form-group input,
.form-group select,
.toolbar-select {
    width: 100%;
    padding: 12px;
    border: 1px solid var(--border);
    background: var(--background);
    color: var(--text);
    border-radius: 8px;
    outline: none;
    font-size: 13px;
    min-width: 0;
}

input:focus,
select:focus {
    border-color: var(--primary);
    box-shadow: 0 0 0 3px rgba(112,45,61,0.08);
}

.form-actions {
    display: flex;
    gap: 10px;
    margin-top: 20px;
}

.add-btn {
    background: var(--primary);
    color: white;
    padding: 12px 24px;
    border: none;
    border-radius: 8px;
    cursor: pointer;
    font-weight: bold;
    transition: 0.3s;
}

.add-btn:hover {
    opacity: 0.85;
    transform: translateY(-2px);
}

.reset-btn {
    padding: 12px 22px;
    border: 1px solid var(--border);
    border-radius: 8px;
    background: var(--soft);
    color: var(--text);
    cursor: pointer;
}

/* TOOLBAR */

.task-toolbar {
    display: flex;
    gap: 12px;
    margin-bottom: 25px;
}

.search-box {
    flex: 1;
    display: flex;
    align-items: center;
    gap: 10px;
    padding: 0 14px;
    border: 1px solid var(--border);
    border-radius: 9px;
    background: var(--card);
    min-width: 0;
}

.search-box span {
    font-size: 24px;
    color: var(--muted);
}

.search-box input {
    border: none;
    outline: none;
    background: transparent;
    color: var(--text);
    width: 100%;
    padding: 13px 0;
}

.search-box input:focus {
    box-shadow: none;
}

.toolbar-select {
    width: 160px;
}

.clear-btn {
    padding: 12px 18px;
    border: 1px solid #E5BFC4;
    border-radius: 8px;
    color: var(--red);
    background: transparent;
    cursor: pointer;
}

/* TASK LIST */

.task-section {
    margin-bottom: 30px;
}

.task-count {
    background: var(--soft);
    color: var(--primary);
    border-radius: 20px;
    padding: 7px 13px;
    font-size: 12px;
}

.task-list {
    display: flex;
    flex-direction: column;
    gap: 12px;
}

.task {
    display: flex;
    align-items: center;
    gap: 15px;
    padding: 18px;
    background: var(--card);
    border: 1px solid var(--border);
    border-left: 5px solid var(--primary);
    border-radius: 12px;
    box-shadow: var(--shadow);
    transition: 0.3s;
}

.task:hover {
    transform: translateY(-2px);
}

.task.completed {
    opacity: 0.65;
}

.task-checkbox {
    width: 20px;
    height: 20px;
    accent-color: var(--primary);
    cursor: pointer;
    flex-shrink: 0;
}

.task-content {
    flex: 1;
    min-width: 0;
}

.task-title {
    font-weight: 600;
    font-size: 15px;
    overflow-wrap: anywhere;
}

.task.completed .task-title {
    text-decoration: line-through;
}

.task-info {
    display: flex;
    gap: 7px;
    flex-wrap: wrap;
    margin-top: 8px;
}

.badge {
    font-size: 11px;
    padding: 5px 9px;
    border-radius: 20px;
    background: var(--soft);
    color: var(--text);
}

.high {
    background: #F4D6D8;
    color: #922F40;
}

.medium {
    background: #F4E5BD;
    color: #806020;
}

.low {
    background: #DCE9DA;
    color: #416747;
}

.overdue {
    background: #F4D6D8;
    color: #922F40;
}

.task-actions {
    display: flex;
    gap: 7px;
    flex-shrink: 0;
}

.action-btn {
    padding: 8px 11px;
    border: none;
    border-radius: 7px;
    cursor: pointer;
}

.edit {
    background: var(--soft);
    color: var(--primary);
}

.delete {
    background: #F4D6D8;
    color: #922F40;
}

.empty {
    text-align: center;
    padding: 50px 15px;
    background: var(--card);
    border: 1px dashed var(--border);
    border-radius: 12px;
    color: var(--muted);
}

.empty div {
    font-size: 45px;
    color: var(--secondary);
    margin-bottom: 12px;
}

.empty h3 {
    color: var(--text);
    margin-bottom: 7px;
}

/* CALENDAR */

.calendar-section {
    margin-top: 35px;
}

.calendar {
    background: var(--card);
    border: 1px solid var(--border);
    padding: 22px;
    border-radius: 14px;
    box-shadow: var(--shadow);
}

.calendar-header {
    display: flex;
    justify-content: space-between;
    align-items: center;
    margin-bottom: 22px;
}

.calendar-header button {
    background: var(--soft);
    color: var(--primary);
    border: none;
    padding: 9px 13px;
    border-radius: 7px;
    cursor: pointer;
}

.calendar-header h3 {
    color: var(--primary);
}

.calendar-grid {
    display: grid;
    grid-template-columns: repeat(7, 1fr);
    gap: 8px;
    text-align: center;
}

.calendar-day {
    padding: 12px 5px;
    border-radius: 8px;
    font-size: 13px;
    min-height: 42px;
    position: relative;
}

.day-name {
    font-weight: bold;
    color: var(--muted);
}

.date-day {
    cursor: pointer;
}

.date-day:hover {
    background: var(--soft);
}

.date-day.today {
    background: var(--primary);
    color: white;
}

.date-day.has-task::after {
    content: "";
    width: 5px;
    height: 5px;
    border-radius: 50%;
    background: var(--secondary);
    position: absolute;
    bottom: 4px;
    left: calc(50% - 2px);
}

.date-day.today.has-task::after {
    background: white;
}

.date-day.selected {
    outline: 2px solid var(--secondary);
}

.calendar-note {
    margin-top: 20px;
    color: var(--muted);
    font-size: 12px;
}

.calendar-note span {
    display: inline-block;
    width: 8px;
    height: 8px;
    background: var(--secondary);
    border-radius: 50%;
    margin-right: 5px;
}

/* FOOTER */

footer {
    text-align: center;
    padding: 30px 10px 10px;
    color: var(--muted);
    font-size: 13px;
    line-height: 2;
}

/* RESPONSIVE */

@media (max-width: 1100px) {

    .sidebar {
        width: 220px;
        min-width: 220px;
    }

    .main-content {
        padding: 25px;
    }

    .form-grid {
        grid-template-columns: repeat(2, 1fr);
    }

    .stats {
        grid-template-columns: repeat(2, 1fr);
    }
}

@media (max-width: 750px) {

    .app {
        flex-direction: column;
    }

    .sidebar {
        width: 100%;
        min-width: 0;
        min-height: auto;
        padding: 15px;
    }

    .logo {
        margin-bottom: 15px;
    }

    .profile {
        display: none;
    }

    .sidebar nav {
        display: flex;
        flex-wrap: wrap;
        gap: 5px;
    }

    .nav-heading {
        width: 100%;
        margin: 10px 5px 5px;
    }

    .nav-btn {
        width: auto;
        margin: 0;
        padding: 9px 11px;
        font-size: 12px;
    }

    .nav-count {
        margin-left: 0;
    }

    .sidebar-bottom {
        margin-top: 12px;
        padding-top: 0;
        display: flex;
        justify-content: space-between;
        align-items: center;
    }

    .theme-toggle {
        width: auto;
        margin: 0;
    }

    .main-content {
        padding: 20px 15px;
    }

    header {
        align-items: flex-start;
        gap: 15px;
    }

    header h1 {
        font-size: 27px;
    }

    .date-box {
        padding: 9px;
    }

    .date-box span {
        display: none;
    }
}

@media (max-width: 500px) {

    .stats {
        grid-template-columns: repeat(2, 1fr);
        gap: 10px;
    }

    .stat-card {
        padding: 12px;
        gap: 9px;
    }

    .stat-icon {
        width: 35px;
        height: 35px;
        font-size: 18px;
    }

    .stat-card h2 {
        font-size: 20px;
    }

    .stat-card p {
        font-size: 11px;
    }

    .form-grid {
        grid-template-columns: 1fr;
    }

    .task-toolbar {
        flex-wrap: wrap;
    }

    .search-box {
        flex-basis: 100%;
    }

    .toolbar-select {
        flex: 1;
    }

    .task {
        align-items: flex-start;
        gap: 10px;
        padding: 13px;
    }

    .task-actions {
        flex-direction: column;
    }

    .action-btn {
        padding: 7px;
    }

    .calendar {
        padding: 12px;
    }

    .calendar-grid {
        gap: 3px;
    }

    .calendar-day {
        padding: 10px 2px;
        font-size: 11px;
    }

    .date-box {
        display: none;
    }
}

```

script.js

```

// GET HTML ELEMENTS

const taskForm = document.getElementById("taskForm");
const taskInput = document.getElementById("taskInput");
const categoryInput = document.getElementById("category");
const priorityInput = document.getElementById("priority");
const dueDateInput = document.getElementById("dueDate");
const editIdInput = document.getElementById("editId");

const taskList = document.getElementById("taskList");
const searchInput = document.getElementById("searchInput");
const sortFilter = document.getElementById("sortFilter");

const submitBtn = document.getElementById("submitBtn");
const resetBtn = document.getElementById("resetBtn");
const clearAllBtn = document.getElementById("clearAllBtn");


// LOAD SAVED TASKS

let tasks = JSON.parse(localStorage.getItem("myTasks")) || [];

let currentFilter = "all";
let currentCategory = "";
let selectedDate = "";


// CALENDAR VARIABLES

let calendarDate = new Date();


// SAVE TASKS

function saveTasks() {
    localStorage.setItem("myTasks", JSON.stringify(tasks));
}


// GET TODAY'S DATE

function getToday() {
    const today = new Date();

    const year = today.getFullYear();
    const month = String(today.getMonth() + 1).padStart(2, "0");
    const day = String(today.getDate()).padStart(2, "0");

    return `${year}-${month}-${day}`;
}


// DISPLAY DATE

function displayDate() {
    const today = new Date();

    const options = {
        weekday: "long",
        year: "numeric",
        month: "long",
        day: "numeric"
    };

    const formattedDate = today.toLocaleDateString("en-IN", options);

    document.getElementById("todayDate").textContent =
        `Today is ${formattedDate}`;

    document.getElementById("headerDate").textContent =
        today.toLocaleDateString("en-IN", {
            day: "numeric",
            month: "short",
            year: "numeric"
        });
}


// FORMAT TASK DATE

function formatDate(date) {
    if (!date) return "No deadline";

    const parts = date.split("-");
    const localDate = new Date(
        Number(parts[0]),
        Number(parts[1]) - 1,
        Number(parts[2])
    );

    return localDate.toLocaleDateString("en-IN", {
        day: "numeric",
        month: "short",
        year: "numeric"
    });
}


// ADD OR EDIT TASK

taskForm.addEventListener("submit", function(event) {

    event.preventDefault();

    const title = taskInput.value.trim();

    if (title === "") {
        alert("Please enter a task name!");
        return;
    }

    const editId = editIdInput.value;

    if (editId) {

        const task = tasks.find(item => item.id === editId);

        if (task) {
            task.title = title;
            task.category = categoryInput.value;
            task.priority = priorityInput.value;
            task.dueDate = dueDateInput.value;
        }

    } else {

        const newTask = {
            id: Date.now().toString(),
            title: title,
            category: categoryInput.value,
            priority: priorityInput.value,
            dueDate: dueDateInput.value,
            completed: false,
            createdAt: Date.now()
        };

        tasks.unshift(newTask);
    }

    saveTasks();
    resetForm();
    renderTasks();
});


// RESET FORM

function resetForm() {
    taskForm.reset();
    editIdInput.value = "";
    submitBtn.textContent = "+ Add Task";
}


// CLEAR FORM BUTTON

resetBtn.addEventListener("click", function() {
    resetForm();
});


// RENDER TASKS

function renderTasks() {

    taskList.innerHTML = "";

    let filteredTasks = [...tasks];

    // FILTER BY STATUS

    if (currentFilter === "pending") {
        filteredTasks = filteredTasks.filter(task => !task.completed);
    }

    if (currentFilter === "completed") {
        filteredTasks = filteredTasks.filter(task => task.completed);
    }

    // FILTER BY CATEGORY

    if (currentCategory) {
        filteredTasks = filteredTasks.filter(
            task => task.category === currentCategory
        );
    }

    // FILTER BY CALENDAR DATE

    if (selectedDate) {
        filteredTasks = filteredTasks.filter(
            task => task.dueDate === selectedDate
        );
    }

    // SEARCH TASKS

    const searchText = searchInput.value.toLowerCase().trim();

    if (searchText) {
        filteredTasks = filteredTasks.filter(task =>
            task.title.toLowerCase().includes(searchText) ||
            task.category.toLowerCase().includes(searchText) ||
            task.priority.toLowerCase().includes(searchText)
        );
    }

    // SORT TASKS

    if (sortFilter.value === "newest") {
        filteredTasks.sort(
            (a, b) => b.createdAt - a.createdAt
        );
    }

    if (sortFilter.value === "oldest") {
        filteredTasks.sort(
            (a, b) => a.createdAt - b.createdAt
        );
    }

    if (sortFilter.value === "priority") {
        const priorityOrder = {
            High: 1,
            Medium: 2,
            Low: 3
        };

        filteredTasks.sort(
            (a, b) =>
                priorityOrder[a.priority] - priorityOrder[b.priority]
        );
    }

    if (sortFilter.value === "date") {
        filteredTasks.sort((a, b) => {
            if (!a.dueDate) return 1;
            if (!b.dueDate) return -1;
            return a.dueDate.localeCompare(b.dueDate);
        });
    }

    // UPDATE TITLE

    if (selectedDate) {
        document.getElementById("listTitle").textContent =
            `Tasks for ${formatDate(selectedDate)}`;
    } else if (currentCategory) {
        document.getElementById("listTitle").textContent =
            `${currentCategory} Tasks`;
    } else {
        const titles = {
            all: "All Tasks",
            pending: "Pending Tasks",
            completed: "Completed Tasks"
        };

        document.getElementById("listTitle").textContent =
            titles[currentFilter];
    }

    document.getElementById("taskSubtitle").textContent =
        "Manage your daily activities.";

    document.getElementById("taskCount").textContent =
        `${filteredTasks.length} Tasks`;


    // DISPLAY EMPTY MESSAGE

    if (filteredTasks.length === 0) {

        taskList.innerHTML = `
            <div class="empty">
                <div>♡</div>
                <h3>No tasks found!</h3>
                <p>Try adding a new task or changing your filters.</p>
            </div>
        `;

    } else {

        filteredTasks.forEach(task => {

            const taskElement = document.createElement("div");

            taskElement.className =
                task.completed ? "task completed" : "task";

            const overdue =
                task.dueDate &&
                task.dueDate < getToday() &&
                !task.completed;

            taskElement.innerHTML = `
                <input
                    type="checkbox"
                    class="task-checkbox"
                    ${task.completed ? "checked" : ""}
                    aria-label="Mark ${escapeHTML(task.title)} as completed"
                >

                <div class="task-content">

                    <p class="task-title">
                        ${escapeHTML(task.title)}
                    </p>

                    <div class="task-info">

                        <span class="badge">
                            ${escapeHTML(task.category)}
                        </span>

                        <span class="badge ${task.priority.toLowerCase()}">
                            ${escapeHTML(task.priority)} Priority
                        </span>

                        <span class="badge ${overdue ? "overdue" : ""}">
                            ${overdue ? "Overdue: " : "Due: "}
                            ${formatDate(task.dueDate)}
                        </span>

                    </div>

                </div>

                <div class="task-actions">

                    <button class="action-btn edit" type="button">
                        ✎
                    </button>

                    <button class="action-btn delete" type="button">
                        ✕
                    </button>

                </div>
            `;

            // COMPLETE TASK

            const checkbox =
                taskElement.querySelector(".task-checkbox");

            checkbox.addEventListener("change", function() {

                task.completed = checkbox.checked;

                saveTasks();
                renderTasks();

            });


            // EDIT TASK

            const editButton =
                taskElement.querySelector(".edit");

            editButton.addEventListener("click", function() {

                taskInput.value = task.title;
                categoryInput.value = task.category;
                priorityInput.value = task.priority;
                dueDateInput.value = task.dueDate;

                editIdInput.value = task.id;

                submitBtn.textContent = "Update Task";

                taskInput.focus();

                window.scrollTo({
                    top: 0,
                    behavior: "smooth"
                });

            });


            // DELETE TASK

            const deleteButton =
                taskElement.querySelector(".delete");

            deleteButton.addEventListener("click", function() {

                if (confirm("Are you sure you want to delete this task?")) {

                    tasks = tasks.filter(
                        item => item.id !== task.id
                    );

                    saveTasks();
                    renderTasks();

                }

            });

            taskList.appendChild(taskElement);

        });

    }

    updateStatistics();
    renderCalendar();

}


// SAFELY DISPLAY USER TEXT

function escapeHTML(value) {
    return String(value).replace(/[&<>"']/g, function(char) {
        const entities = {
            "&": "&amp;",
            "<": "&lt;",
            ">": "&gt;",
            '"': "&quot;",
            "'": "&#39;"
        };

        return entities[char];
    });
}


// UPDATE STATISTICS

function updateStatistics() {

    const total = tasks.length;

    const completed = tasks.filter(
        task => task.completed
    ).length;

    const pending = total - completed;

    const overdue = tasks.filter(task =>
        task.dueDate &&
        task.dueDate < getToday() &&
        !task.completed
    ).length;

    document.getElementById("totalTasks").textContent = total;

    document.getElementById("completedTasks").textContent =
        completed;

    document.getElementById("pendingTasks").textContent =
        pending;

    document.getElementById("overdueTasks").textContent =
        overdue;

    document.getElementById("allCount").textContent = total;

    document.getElementById("pendingCount").textContent =
        pending;

    document.getElementById("completedCount").textContent =
        completed;

    // PROGRESS BAR

    let progress = total === 0
        ? 0
        : Math.round((completed / total) * 100);

    document.getElementById("progressPercent").textContent =
        progress + "%";

    document.getElementById("progressBar").style.width =
        progress + "%";
}


// SIDEBAR FILTERS

document.querySelectorAll(".nav-btn").forEach(button => {

    button.addEventListener("click", function() {

        document.querySelectorAll(".nav-btn").forEach(btn => {
            btn.classList.remove("active");
        });

        this.classList.add("active");

        selectedDate = "";

        if (this.dataset.filter) {

            currentFilter = this.dataset.filter;
            currentCategory = "";

        } else if (this.dataset.category) {

            currentCategory = this.dataset.category;
            currentFilter = "all";

        }

        renderTasks();

    });

});


// SEARCH

searchInput.addEventListener("input", renderTasks);


// SORT

sortFilter.addEventListener("change", renderTasks);


// CLEAR ALL TASKS

clearAllBtn.addEventListener("click", function() {

    if (tasks.length === 0) {
        alert("There are no tasks to clear!");
        return;
    }

    if (confirm("Are you sure you want to delete all tasks?")) {

        tasks = [];

        saveTasks();
        resetForm();

        selectedDate = "";
        currentCategory = "";
        currentFilter = "all";

        document.querySelectorAll(".nav-btn").forEach(btn => {
            btn.classList.remove("active");
        });

        document.querySelector('[data-filter="all"]')
            .classList.add("active");

        renderTasks();

    }

});


// DARK MODE

const themeToggle = document.getElementById("themeToggle");

const themeIcon = document.getElementById("themeIcon");

const themeText = document.getElementById("themeText");

function updateThemeButton() {

    const isDark = document.body.classList.contains("dark");

    themeIcon.textContent = isDark ? "☀" : "☾";

    themeText.textContent = isDark
        ? "Light Mode"
        : "Dark Mode";

}

const savedTheme = localStorage.getItem("plannerTheme");

if (savedTheme === "dark") {
    document.body.classList.add("dark");
}

updateThemeButton();

themeToggle.addEventListener("click", function() {

    document.body.classList.toggle("dark");

    const theme = document.body.classList.contains("dark")
        ? "dark"
        : "light";

    localStorage.setItem("plannerTheme", theme);

    updateThemeButton();

});


// CALENDAR

function renderCalendar() {

    const year = calendarDate.getFullYear();
    const month = calendarDate.getMonth();

    const monthNames = [
        "January", "February", "March", "April",
        "May", "June", "July", "August",
        "September", "October", "November", "December"
    ];

    document.getElementById("monthYear").textContent =
        `${monthNames[month]} ${year}`;

    const grid = document.getElementById("calendarGrid");

    grid.innerHTML = "";

    const days = ["Sun", "Mon", "Tue", "Wed", "Thu", "Fri", "Sat"];

    // DAY NAMES

    days.forEach(day => {

        const dayElement = document.createElement("div");

        dayElement.className = "calendar-day day-name";

        dayElement.textContent = day;

        grid.appendChild(dayElement);

    });


    // FIRST DAY OF MONTH

    const firstDay = new Date(year, month, 1).getDay();

    // TOTAL DAYS IN MONTH

    const totalDays = new Date(year, month + 1, 0).getDate();

    // EMPTY SPACES

    for (let i = 0; i < firstDay; i++) {

        const emptyDay = document.createElement("div");

        grid.appendChild(emptyDay);

    }


    // DISPLAY DATES

    for (let day = 1; day <= totalDays; day++) {

        const dateElement = document.createElement("div");

        const monthString = String(month + 1).padStart(2, "0");
        const dayString = String(day).padStart(2, "0");

        const dateString =
            `${year}-${monthString}-${dayString}`;

        dateElement.className = "calendar-day date-day";

        dateElement.textContent = day;

        // TODAY

        if (dateString === getToday()) {
            dateElement.classList.add("today");
        }

        // TASK DOT

        const hasTask = tasks.some(
            task => task.dueDate === dateString
        );

        if (hasTask) {
            dateElement.classList.add("has-task");
        }

        // SELECTED DATE

        if (selectedDate === dateString) {
            dateElement.classList.add("selected");
        }

        // CLICK DATE

        dateElement.addEventListener("click", function() {

            selectedDate =
                selectedDate === dateString ? "" : dateString;

            currentFilter = "all";
            currentCategory = "";

            document.querySelectorAll(".nav-btn").forEach(btn => {
                btn.classList.remove("active");
            });

            document.querySelector('[data-filter="all"]')
                .classList.add("active");

            renderTasks();

            document.querySelector(".task-section").scrollIntoView({
                behavior: "smooth",
                block: "start"
            });

        });

        grid.appendChild(dateElement);

    }

}


// PREVIOUS MONTH

document.getElementById("prevMonth").addEventListener("click", function() {

    calendarDate.setMonth(calendarDate.getMonth() - 1);

    renderCalendar();

});


// NEXT MONTH

document.getElementById("nextMonth").addEventListener("click", function() {

    calendarDate.setMonth(calendarDate.getMonth() + 1);

    renderCalendar();

});


// INITIALIZE WEBSITE

displayDate();
renderTasks();

```


## OUTPUT

<img width="1920" height="1080" alt="image" src="https://github.com/user-attachments/assets/20d6951b-a18b-4df7-836d-74b86f2bce5b" />

<img width="1920" height="1080" alt="image" src="https://github.com/user-attachments/assets/ef66ab2a-2a2d-46ad-857f-8b2d14dba069" />


## RESULT
The program for creating To-do list using JavaScript is executed successfully.

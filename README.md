class TaskManager:
    def __init__(self):
        self.tasks = []
    
    def add_task(self, task):
        # Add a new task to the list
        self.tasks.append({"task": task, "completed": False})
        print(f"Task '{task}' added successfully!")
    
    def view_tasks(self):
        # Display all tasks with their status
        if not self.tasks:
            print("No tasks found! Add some tasks to get started.")
            return
        
        print("\n" + "="*50)
        print("YOUR TASKS")
        print("="*50)
        for i, task in enumerate(self.tasks, 1):
            status = "✓" if task["completed"] else "○"
            print(f"{i:2d}. {status} {task['task']}")
        print("="*50)
    
    def complete_task(self, task_number):
        # Mark a task as completed
        try:
            if self.tasks[task_number - 1]["completed"]:
                print("This task is already completed!")
                return
            
            self.tasks[task_number - 1]["completed"] = True
            task_name = self.tasks[task_number - 1]["task"]
            print(f"Task '{task_name}' marked as completed!")
        except IndexError:
            print("Invalid task number, please try again.")

#example usage
if __name__ == "__main__":
    # Create a task manager instance
    tm = TaskManager()
    
    # Add some tasks
    tm.add_task("Buy groceries")
    tm.add_task("Finish homework")
    tm.add_task("Call mom")
    
    # View tasks
    tm.view_tasks()
    
    # Complete a task
    tm.complete_task(1)
    
    # View tasks again
    tm.view_tasks()

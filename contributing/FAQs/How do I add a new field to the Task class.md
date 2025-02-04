# How do I add a new field to the Task class?

- In [tests/Task.test.ts](https://github.com/obsidian-tasks-group/obsidian-tasks/blob/main/tests/Task.test.ts):
  - Add a new failing block to the `'identicalTo'` section.
  - Here is an existing example: ['should check path'](https://github.com/obsidian-tasks-group/obsidian-tasks/blob/5b0831c36a80c4cde2d64a6cd281bb4b51e9a142/tests/Task.test.ts#L834-L840).
- In [src/Task.ts](https://github.com/obsidian-tasks-group/obsidian-tasks/blob/main/src/Task.ts), update `Task.identicalTo()`:
  - Once you have a failing test in [tests/Task.test.ts](https://github.com/obsidian-tasks-group/obsidian-tasks/blob/main/tests/Task.test.ts), implement the check for changed value of your new field in `Task.identicalTo()`.
  - This important method is used to detect whether any edits of any kind have been made to a task, to detect whether task block results need to be updated.
  - Here is the code for the method as of 2022-11-12:
    - [Task.identicalTo() in 5b0831c36a80c4cde2d64a6cd281bb4b51e9a142](https://github.com/obsidian-tasks-group/obsidian-tasks/blob/5b0831c36a80c4cde2d64a6cd281bb4b51e9a142/src/Task.ts#L732-L802)
- In [tests/TestingTools/TaskBuilder.ts](https://github.com/obsidian-tasks-group/obsidian-tasks/blob/main/tests/TestingTools/TaskBuilder.ts):
  - Add the new field and a corresponding method.
  - Keep the same field order as in the `Task` class.
  - Update the `build()` method.
- In [tests/TestingTools/TaskBuilder.test.ts](https://github.com/obsidian-tasks-group/obsidian-tasks/blob/main/tests/TestingTools/TaskBuilder.test.ts):
  - If the code in TaskBuild will be non-trivial, first add a failing test for it.


Now that you've seen manual exploratory testing, the logical next step is functional testing, which takes the parts of the exploratory testing that check the code worked as expected and gives them a structure that will be useful later when testing is automated.  
现在您已经了解了手动探索性测试，接下来的合乎逻辑的步骤是功能测试，它将探索性测试中验证代码是否按预期工作的部分结构化，这在后续的自动化测试中会非常有用。  

You might come out of your manual testing phase with some simple testing code.  
在手动测试阶段结束时，您可能会得到一些简单的测试代码。  

And here's the example that you saw in the previous video for the todo list app.  
以下是您在上一视频中看到的待办事项列表应用的示例。  

The example usage code here tests all of the various functions of the todo list app code and does explore some edge cases.  
示例代码测试了待办事项列表应用代码的所有功能，并探索了一些边界情况。  

Code like this could have been written by you as you developed or by a human tester, or be suggested by an LLM working with you as a pair programmer.  
这样的代码可能是您在开发时编写的，也可能是人类测试人员编写的，或者是与您协作的大语言模型（LLM）提出的建议。  

The goal of functional testing is to check the application's functionality against predefined requirements.  
功能测试的目标是根据预定义的需求验证应用程序的功能性。  

It's a crucial step for verifying that the application performs correctly and according to specifications.  
这是验证应用程序是否按规范正确运行的重要步骤。  

For this kind of testing, you'll write test cases to ensure each function of your code does work as expected, and LLMs are really good at this.  
在这种测试中，您需要编写测试用例以确保代码的每个功能按预期运行，而 LLM 在这方面表现非常出色。  

![image](https://github.com/user-attachments/assets/4bc5be5f-d336-4cc3-90b6-3dcdd7d0c5c5)


![image](https://github.com/user-attachments/assets/36f7b4cc-b855-4acf-a657-8fc42a481685)


With a prompt like this one, you can give an LLM your code and the test that came out of your exploratory testing, and you can ask it to apply a structure that makes it useful for more formal testing.  
通过这样的提示，您可以将代码和探索性测试生成的测试提供给 LLM，并请求它应用一种更适合正式测试的结构。  

And this is where your own expertise can help you quickly get the code you need.  
在这里，您的专业知识可以帮助您快速获得所需的代码。  

For instance, by specifying that you wanted to write tests using the `unittest` package.  
例如，您可以指定希望使用 `unittest` 包编写测试。  

And of course, if you aren't sure of a good package that you could use, you can always chat with the LLM and have it recommend options to you.  
当然，如果您不确定可以使用的优秀包，您可以随时与 LLM 对话，获取推荐选项。  


#### Practice

Take the usage tests you came up with in the previous video, or use the code in `tasks2.py` in the downloads for this video, and work with an LLM to implement a set of functional tests for those usage cases using the `unittest` module in Python.  
使用您在上一视频中设计的测试用例，或者使用本视频下载中提供的 `tasks2.py` 代码，与 LLM 协作，使用 Python 的 `unittest` 模块为这些用例实现一组功能测试。  

Then in the Coursera lab environment, or Google Colab, or on your own machine, try running the test cases that the LLM wrote.  
然后，在 Coursera 实验环境、Google Colab 或您自己的计算机上，尝试运行 LLM 编写的测试用例。  

When you’re done, come back to see how the LLM responded to Laurence, and how the tests that it wrote work in a code walkthrough.  
完成后，回来看看 LLM 如何回应 Laurence，以及它编写的测试在代码演示中是如何工作的。  

#### Response from LLM
And here's the `unittest` code that the LLM wrote.  
以下是 LLM 编写的 `unittest` 代码。  

You can see several test cases to check the different functionalities of your application.  
您可以看到几个测试用例用于检查应用程序的不同功能。  

In fact, the model has designed a test for each of the example use cases that you gave it in the prompt.  
实际上，模型为您在提示中提供的每个示例用例都设计了一个测试。  

The model also created a setup method that ensures you start with a clean slate before each test.  
模型还创建了一个 `setup` 方法，以确保每次测试前都有一个干净的测试环境。  

Now this is important so you can avoid side effects between different tests.  
这是很重要的，因为它可以避免不同测试之间的相互影响。  

In the `test_add_task` method, you check if a task is added successfully and then you verify that it appears in the task list.  
在 `test_add_task` 方法中，您会检查任务是否成功添加，并验证它是否出现在任务列表中。  

For `test_remove_task`, you add the task first and then remove it to check if it's removed from the list.  
在 `test_remove_task` 方法中，您先添加任务，然后删除它以检查它是否从列表中移除。  

The `test_remove_nonexistent_task` method verifies that trying to remove a non-existent task will return the correct message.  
`test_remove_nonexistent_task` 方法验证尝试删除不存在的任务是否会返回正确的消息。  

The `test_list_tasks` method checks if the list of tasks is returned correctly.  
`test_list_tasks` 方法检查任务列表是否正确返回。  

And `test_add_empty_task` checks if the application handles adding an empty task.  
`test_add_empty_task` 方法检查应用程序是否处理添加空任务的情况。  

Remember, if you have any questions about how the `unittest` module works, be sure to ask the LLM follow-up questions so that you can understand the code and know how to use it properly.  
请记住，如果您对 `unittest` 模块的工作方式有任何疑问，一定要向 LLM 提出后续问题，以便理解代码并正确使用。  

The next step is to try out the code that the LLM wrote.  
下一步是尝试运行 LLM 编写的代码。  

So just like before, we have our simple task list and three functions to add, remove, and list tasks.  
就像之前一样，我们有一个简单的任务列表和三个函数用于添加、删除和列出任务。  

Over here we have a new class designed to unit test that code.  
这里我们有一个新类用于对这些代码进行单元测试。  

There are multiple test cases here, like adding a task, removing a task, removing a non-existent task, and so on.  
这里有多个测试用例，例如添加任务、删除任务、删除不存在的任务等。  

If I run this and I look at my tests, we'll see that all of my tests have passed.  
如果我运行这些测试并查看结果，会发现所有测试都通过了。  

Now that might look like it's a good thing, but let's think about this for a second and let's think about what has actually happened here.  
这看起来是好事，但让我们稍微想一想，这里实际上发生了什么。  

So we can see that I'm testing that I'm adding an empty task, and I'm checking to see if adding an empty task returns "task blank added," and that passes.  
可以看到，我正在测试添加一个空任务，并检查添加空任务是否返回“task blank added”，这确实通过了测试。  

But requirements-wise, if we're building a task list, do we really want to be able to add an empty task?  
但从需求角度来看，如果我们构建一个任务列表，我们真的希望能够添加空任务吗？  

I think the answer to that should be no.  
我认为答案应该是否定的。  

The functionality is not what we want.  
这个功能并不是我们想要的。  

And this is why manual testing—exploring testing yourself by going through the code and thinking of task cases—ends up being really, really useful.  
这就是为什么手动测试——通过检查代码并思考测试用例来探索测试——最终会非常有用的原因。  

Because ultimately, we probably want to put a check in here to see if the task is empty.  
因为最终，我们可能需要在这里添加一个检查，判断任务是否为空。  

And if the task is empty, we should reject the adding of the task and then return an error message of some type.  
如果任务为空，我们应该拒绝添加该任务，并返回某种类型的错误消息。  

And then our testing should test for that error message.  
然后我们的测试应该验证该错误消息。  

Again, this is a great example where simply trusting an LLM can get you into trouble.  
再次说明，单纯信任 LLM 会让您陷入困境。  

And that's why I would always encourage you not to get lazy and not to rely on them too much, even as they get more and more advanced and capable.  
这也是为什么我总是鼓励您不要懒惰，不要过于依赖它们，即使它们变得越来越先进和强大。  

At this point, to test yourself, try pausing the video and updating the todo list code to disallow adding an empty task.  
此时，为了测试您自己，尝试暂停视频并更新待办事项列表代码，以禁止添加空任务。  

And once you've done that, go on and update the test case to only pass if it sees the correct error coming back when you try adding that empty task.  
完成后，继续更新测试用例，只有当尝试添加空任务时收到正确的错误消息时，测试才通过。  

#### Practice

Working with an LLM or doing it yourself, update the code to disallow adding an empty task. Then update the test case for adding an empty task to make sure it responds correctly when trying to add an empty task.

---

One more thing, it's important to maintain and update your test cases as the application evolves.  
还有一点，随着应用程序的演变，维护和更新测试用例非常重要。  


Whenever new features are added or existing ones are modified, you should write new tests or update existing ones to cover these changes.  
每当添加新功能或修改现有功能时，您都应该编写新测试或更新现有测试以涵盖这些变化。  

This helps ensure that your application remains reliable over time, and this maintenance work is a great place where the LLM yet again can be your friend.  
这有助于确保您的应用程序随时间保持可靠性，而这项维护工作再次成为 LLM 的用武之地。  

You can give it the updated code and the current test cases and have it help you figure out how to update your test cases, adding, editing, or removing as necessary.  
您可以将更新的代码和当前的测试用例提供给它，让它帮助您更新测试用例，根据需要添加、编辑或删除。  

Functional testing ensures that your application behaves as expected under predefined conditions.  
功能测试确保您的应用程序在预定义条件下按预期运行。  

And it's important to get these tests right, because many of your colleagues, especially those responsible for maintaining your application in production, rely on them to work well so they can do their jobs effectively.  
确保这些测试正确非常重要，因为您的许多同事，尤其是负责在生产环境中维护应用程序的同事，需要依赖这些测试的良好运行来有效完成他们的工作。  

And as you've seen, an LLM is really useful for writing good manual tests.  
正如您所见，LLM 在编写良好的手动测试方面非常有用。  

But these alone will never be enough for large code bases.  
但仅靠这些对于大型代码库来说永远不够。  

In the real world, automated testing is critical.  
在现实世界中，自动化测试至关重要。  

So let's go on to the next video to look at how an LLM can make automated testing easier for you and for your entire team.  
让我们进入下一个视频，看看 LLM 如何使自动化测试对您和整个团队更简单。  

---

6 minutes, 1032 words

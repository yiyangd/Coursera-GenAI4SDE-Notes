
### Intro
As you saw in the previous video, there are lots of issues to think through and address in testing, even with very simple apps like the Flask endpoint example.  
如您在前一个视频中所见，即使是像 Flask 端点示例这样非常简单的应用程序，也有许多问题需要仔细思考和解决。  

At early stages of development, you'll likely focus on manual testing, where you are a tester, work with the code and can test without automated tools.  
在开发的早期阶段，您可能会专注于手动测试，此时您充当测试人员，与代码交互并在没有自动化工具的情况下进行测试。  


![image](https://github.com/user-attachments/assets/5ec21294-1c5f-4338-a53d-edb0390a7f78)

Software testers break down manual testing into many subtypes, as specificity can help create more effective, efficient testing processes.  
软件测试人员将手动测试细分为许多子类型，因为具体化可以帮助创建更有效率的测试流程。  

By working with an LLM to think through different types of testing activities, you can make life much easier for anyone testing your code.  
通过与大语言模型（LLM）合作思考不同类型的测试活动，您可以大大简化测试人员的工作。  

In this video, you're going to dive into one of the most important types of manual testing: exploratory testing.  
在本视频中，您将深入了解手动测试中最重要的类型之一：探索性测试。  

You'll work with an LLM to implement this strategy in Python.  
您将使用 LLM 在 Python 中实现这一策略。  

### 2. Exploratory Testing
Exploratory testing is a relatively informal mode of testing where you explore the application you're developing without predefined test cases.  
探索性测试是一种相对非正式的测试方式，在这种测试中，您无需预定义测试用例即可探索正在开发的应用程序。  

The goal is to discover bugs by using the application in the way a user would.  
目标是通过以用户的方式使用应用程序来发现漏洞。  

If that sounds random, well, it really is, but it's good to put yourself in your user's shoes and work in the same ways that they might.  
如果这听起来很随意，实际上确实如此，但将自己置于用户的角度并以他们可能的方式操作是有益的。  

To think through how exploratory testing might play out, you're going to use a very simple to-do list application built in Python.  
为了思考探索性测试可能的展开方式，您将使用一个非常简单的 Python 待办事项列表应用程序。  

Here's the code.  
以下是代码。  

```python
tasks = []

def add_task(task):
    tasks.append(task)
    return f"Task '{task}' added."

def remove_task(task):
    if task in tasks:
        tasks.remove(task)
        return f"Task '{task}' removed."
    else:
        return "Task not found."

def list_tasks():
    return tasks

# Example usage
print(add_task("Buy groceries"))
print(add_task("Read a book"))
print(list_tasks())
print(remove_task("Read a book"))
print(list_tasks())
```

If you were to consume an API like this, what kind of things would you do to test to see if it works?  
如果您要使用这样的 API，您会进行哪些测试来验证它是否正常工作？  

Its functions include things like adding tasks, removing tasks, and listing tasks.  
它的功能包括添加任务、移除任务和列出任务。  

So it would make sense for you to try each one of these.  
因此，尝试每一项功能是有意义的。  

Here's an example usage code.  
以下是一个使用示例代码。  

First, you'd like to add some tasks, like buy groceries or read a book.  
首先，您可以添加一些任务，比如“购买食品”或“阅读书籍”。  

Then you'd use the `list_tasks` method to see if they're listed correctly.  
然后您可以使用 `list_tasks` 方法查看它们是否正确列出。  

Then maybe you'd try removing a task and then check the task list again to verify that your task was removed properly.  
接着，您可能会尝试移除一个任务，然后再次检查任务列表以验证任务是否已正确移除。  

These are fairly straightforward tests that the methods will work as you expect them to.  
这些是相当直接的测试，方法会按您的预期工作。  

Next, you might move on to testing some edge cases.  
接下来，您可以测试一些边界情况。  

For instance, what happens when you try to remove a task that doesn't exist?  
例如，当您尝试移除一个不存在的任务时会发生什么？  

Well, you can see that the `remove_task` method should tell us that the task isn't found, so let's just test that and make sure.  
您会看到 `remove_task` 方法应该告诉我们任务未找到，因此让我们测试这一点以确保其正确性。  


```python
print(remove_task("Go for a run")) # Output: Task not found.
```


Now, think about some of the use cases that you might try.  
现在，思考您可能尝试的一些用例。  

Pause the video and try coding them for yourself.  
暂停视频，尝试自己编写代码。  

The code is available for you in the download for these courses. It's called `tasks.py`.  
课程提供的下载中包含该代码，文件名为 `tasks.py`。  

Or you could generate one that's similar with an LLM if you don't want to code it yourself.  
或者，如果您不想自己编写代码，可以使用 LLM 生成一个类似的代码。  

#### Practice (2:24)


Download the `tasks.py` todo list code from the video downloads.  
从视频下载中下载 `tasks.py` 待办事项列表代码。  

Think through some exploratory test cases, like the ones that Laurence discusses in the video, and try writing some code to carry them out.  
思考一些探索性测试用例，例如视频中 Laurence 讨论的那些，并尝试编写一些代码来执行它们。  

Be sure to note any unusual or unexpected behavior that you find in your exploratory testing.  
请务必记录您在探索性测试中发现的任何异常或意外行为。  

Then pass the `tasks.py` code to an LLM (without any tests) and ask it to behave as a software tester or similar role and to come up with some test cases of the type that would be written during manual exploratory testing.  
然后将 `tasks.py` 代码（不包含任何测试）传递给 LLM，并要求其以软件测试人员或类似角色的身份生成一些在手动探索性测试期间会编写的测试用例。  

Compare the tests and code that the LLM generates to your own list, and try any updated code the LLM creates.  
将 LLM 生成的测试和代码与您自己的列表进行比较，并尝试运行 LLM 创建的任何更新代码。  

When you’re done, come back to see how the LLM responded to Laurence.  
完成后，回来查看 LLM 对 Laurence 的响应。  

### 3. 
How did that go?  
效果如何？  

Hopefully, you came up with some ideas, and there's one issue that you may have found, and it's not immediately obvious, and that is you can add an empty task.  
希望您提出了一些想法，并且您可能发现了一个问题，这个问题并不显而易见，那就是您可以添加一个空任务。  

Then when you list out the tasks, you're going to get that empty spot in the list, and that's probably something you would want to fix.  
然后，当您列出任务时，列表中会出现一个空白，这可能是您希望修复的问题。  

That's some of the essence of exploratory testing.  
这就是探索性测试的精髓之一。  

Experienced software testers are really good at this type of free-form testing, but you won't always have a dedicated tester with you at the early stages of your project.  
经验丰富的软件测试人员擅长这种自由形式的测试，但在项目早期阶段，您未必总能有专职测试人员与您协作。  



What happens if you try to replicate what you just saw here using an LLM to help you?  
如果您尝试使用 LLM 来帮助复制刚才的测试场景，会发生什么？  

![image](https://github.com/user-attachments/assets/e4070f98-8c0f-4516-aafd-26ad8924a4e0)


In this prompt, I assigned the LLM two roles: a software engineer and a tester, and I ask you to explore the possible edge cases of the code that could cause problems.  
在这个提示中，我为 LLM 分配了两个角色：软件工程师和测试人员，并要求其探索代码中可能导致问题的边界情况。  

Then, if I include the code for it to analyze, we'll see how the model responded.  
然后，如果我提供代码供其分析，我们将看到模型的响应。  

#### Responses

Let's take a look at what ChatGPT came back with.  
让我们看看 ChatGPT 的反馈结果。  

ChatGPT found a number of issues and suggested some potential improvements.  
ChatGPT发现了一些问题并建议了一些潜在的改进。  

For example, one of them, global variable usage, I have a global list `tasks`, which could cause issues if the module is used multiple times or in a multi-threaded environment.  
例如，其中一个问题是全局变量的使用。我有一个全局列表 `tasks`，如果模块被多次使用或在多线程环境中运行，这可能会引发问题。  

We'll get back to multi-threaded in a moment.  
稍后我们将回到多线程的问题。  

The function return types could also return a string saying task not found if the task is not found, but returns a task list if it is found. This is inconsistent return types.  
函数返回类型也可能存在问题：如果任务未找到，会返回一个字符串“任务未找到”；而如果任务找到，则返回任务列表。这是一种不一致的返回类型。  

There's various other things, such as task duplication. It does not check for duplicate tasks when we do `add_task`.  
还有其他问题，比如任务重复。在执行 `add_task` 时，它没有检查任务是否重复。  

It doesn't handle an empty task or when none is done.  
它没有处理空任务或无任务完成的情况。  

The more interesting one to me is thread safety.  
我觉得更有趣的是线程安全性问题。  

I never thought about this, but the current implementation is not thread-safe.  
我之前没有想到这一点，但当前实现并不是线程安全的。  

In a multi-user environment, a lot of people are using this; modifications to the task lists could, of course, lead to race conditions.  
在多用户环境中，很多人使用这个程序；对任务列表的修改可能会导致竞争条件。  

The suggestion is to use thread locking to ensure thread safety.  
建议使用线程锁来确保线程安全。  

Then, of course, testing for edge cases. I didn't put any tests in despite this course being all about testing.  
然后当然是测试边界情况。尽管本课程是关于测试的，但我没有编写任何测试。  

The suggestion, of course, is to add unit tests.  
建议是添加单元测试。  

It ends up giving me a revised version of the code that addresses the above issues, so things such as threading, to be able to handle that, things such as checking for tasks to be none, all of that good stuff.  
最终，它给出了一个修订版代码，解决了上述问题，比如处理线程、检查任务是否为空等。  

Then here at the bottom, the model has included some sample usage code, which looks a lot like the human-written exploratory testing code you saw earlier.  
接着，在底部，模型还包含了一些示例使用代码，看起来与之前您看到的人类编写的探索性测试代码非常相似。  

It's creating a task list, adding tasks, listing them, removing them, and then printing the results.  
它创建了一个任务列表，添加任务，列出任务，移除任务，然后打印结果。  

As you can see, the LLM is great at coming up with the example usage code that's the typical outcome of exploratory testing.  
可以看出，LLM 非常擅长生成作为探索性测试典型结果的示例使用代码。  

Working like this can help you identify edge cases and unusual behavior early in the process.  
以这种方式工作可以帮助您在过程中早期发现边界情况和异常行为。  

By developing with testing in mind, you'll make life easier for your colleagues when you pass the code onto them.  
通过将测试作为开发的一个考虑因素，您可以让代码传递给同事时更加轻松。  

The next step in manual testing is to formalize the outcome of exploratory testing as a set of functional tests.  
手动测试的下一步是将探索性测试的结果形式化为一组功能测试。  

Join me in the next video to see how an LLM can help you with just that.  
在下一视频中加入我，了解 LLM 如何帮助您完成这一过程。  

---


981 words, 5.5 minutes

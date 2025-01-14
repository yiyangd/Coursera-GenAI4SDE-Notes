Automated testing is a natural extension of the functional testing that you explored in the last video.
自动化测试是上一视频中探索的功能测试的自然延伸。

Manual functional testing ensures that individual functions of your code will work as expected, but it can be time-consuming and prone to human error.
手动功能测试可以确保代码的每个功能按预期运行，但这可能耗时且容易出现人为错误。

Automated testing uses software tools to carry out these repetitive tasks automatically, saving you time and ensuring consistency.
自动化测试使用软件工具自动完成这些重复性任务，节省时间并确保一致性。

Automated tests can be run frequently, providing quick feedback and the ability to catch issues early.
自动化测试可以频繁运行，提供快速反馈并能够及早发现问题。

This is especially important as your codebase grows and you make changes to existing functionality.
随着代码库的增长以及现有功能的更改，这一点尤其重要。

Automated testing helps maintain the quality and reliability of your software over time.
自动化测试有助于在时间推移中保持软件的质量和可靠性。

Since Python is the working language in this course, you're going to be using pytest for automated testing.  
由于本课程的工作语言是 Python，您将使用 pytest 进行自动化测试。

Pytest is a powerful and flexible testing framework for Python.  
Pytest 是一个功能强大且灵活的 Python 测试框架。

It makes it easy to write simple and scalable test cases.
它使得编写简单且可扩展的测试用例变得容易。

It also comes with a lot of useful features right out of the box, such as fixtures and parameterized testing.
它还提供了许多开箱即用的有用功能，例如固定装置（fixtures）和参数化测试（parameterized testing）。

Similar frameworks do exist in other languages, and I'll say a little bit more about that later on.
其他语言中也有类似的框架，我将在后面稍作介绍。

Here's a quick refresher on that simple to-do list scenario.
以下是关于简单待办事项列表场景的快速回顾。

You're going to be using a simple list as your data structure to store all of these to-do tasks.
您将使用一个简单的列表作为数据结构来存储所有的待办任务。

The app will include methods that allow you to add or remove tasks from your to-do list.
该应用将包括允许您添加或删除待办事项的方法。

You can then also print out your tasks or you can just clear the whole to-do list.
然后，您还可以打印出任务列表，或者直接清空整个待办事项列表。

Previously, you tested this function using unittest, and here's the code that you saw in the last video for the functional tests of adding and removing tasks, including the edge case of removing a non-existent task.
之前，您使用 unittest 测试了此功能，以下是上一视频中您看到的功能测试代码，包括添加和删除任务的测试以及删除不存在任务的边界情况。

Now let's take a look at how you could build the same tests using pytest.
现在让我们来看看如何使用 pytest 构建相同的测试。

You'll need to install pytest for this next section.
在接下来的部分中，您需要安装 pytest。

You can do this by running pip install pytest in your terminal if you're running locally.
如果您在本地运行，可以在终端中运行 pip install pytest 来安装。

If you're using the Coursera coding environment or Google Colab, it's already installed for you.
如果您使用的是 Coursera 编程环境或 Google Colab，则已经为您安装好了。

Pytest can automatically discover and run your tests, providing a clean and readable output.
Pytest 可以自动发现并运行您的测试，并提供清晰且可读的输出。

The tests can be included directly in your Python code scripts or in separate files in your subdirectory, prefixed with the name tests.
测试可以直接包含在您的 Python 代码脚本中，或者存放在子目录中以 tests 为前缀的单独文件中。

One way that pytest automatically discovers tests is by looking for functions within your code that are prefixed with the word test.
Pytest 自动发现测试的一种方法是查找代码中以 test 为前缀的函数。

For simplicity, we're going to follow that convention here.
为了简单起见，我们将在此遵循这一约定。

Here's some code where I've added a couple of pytest test functions for the to-do list.
以下是我为待办事项列表添加的几个 pytest 测试函数的代码。

First, to test whether you're adding a task correctly, and then to see if you're listing all of the tasks correctly.
首先，测试您是否正确添加了任务，然后检查是否正确列出了所有任务。

I've deliberately included a bug here. Can you see it? Pause the video for a second if you need to.
我在这里故意加入了一个错误。您能发现吗？如果需要，请暂停视频稍作思考。

Now, if you run this with pytest, you'll get output like this.
现在，如果您使用 pytest 运行代码，您会看到如下输出。

Notice that there are only two tests, but only one of those passed.
注意，这里只有两个测试，但只有一个通过了。

For the one that failed, we're going to get some details as to why.
对于失败的那个测试，我们会得到一些失败原因的详细信息。

You can see that I misspelled "groceries" in my test case.
您可以看到，我在测试用例中拼错了 “groceries”。

Now, don't worry if you didn't catch that one when you inspected the code.
如果您在检查代码时没有发现这个错误，不要担心。

This is why automated testing is so helpful.
这就是为什么自动化测试非常有用的原因。



Now that you have a sense of how pytest works, let's bring the LLM back into the process.  
现在您已经了解了 pytest 的工作原理，让我们将 LLM 引入这个过程。  

Now, with a prompt that assigns a role, you can get GPT to help you build your test suite.  
通过一个带有角色分配的提示，您可以让 GPT 帮助您构建测试套件。  

Here, you're asking the model to bring expert-level pytest knowledge to the table to write a comprehensive set of tests for the to-do list code.  
在这里，您请求模型以专家级的 pytest 知识为待办事项代码编写一组全面的测试。  

Run this, and GPT should return some nice test code for you.  
运行后，GPT 应该会为您返回一些优秀的测试代码。  

Let's take a look at what it created for me.  
让我们看看它为我生成了什么。  

Let's take a look at the notebook, and we can look at some of the new things that we've added to the notebook for handling things, for example, adding an empty task.  
让我们看看笔记本中新增的内容，例如处理添加空任务的情况。  

One of the interesting things about this one is good Python coding here; we can see that if we try to add an empty task, what we want to do is raise an error when that happens.  
这段代码的一个有趣之处在于它展现了良好的 Python 编码实践：如果我们尝试添加一个空任务，理想情况下应该引发错误。  

Now when we're doing our testing, instead of just checking for values, we also want to be checking for errors.  
在测试时，我们不仅需要检查值，还需要检查错误。  

Then similarly for the `remove_task`, we want to just say when there's a task there, we're going to go through the tasks and remove that.  
类似地，对于 `remove_task` 方法，如果任务存在，我们会遍历任务列表并将其删除。  

But in this case, if there's no task there, we're just going to return a string.  
但如果任务不存在，我们将只返回一个字符串。  

There's two different cases here: one where we raise an error, one where we just return a string, and we want to take a look at the test cases for these things.  
这里有两种不同的情况：一种是引发错误，另一种是返回字符串，我们需要为这两种情况编写测试用例。  

Here, we could have just used the string and not appended the task, or here we could have just returned an error, but I just wanted to cover both examples.  
这里我们可以只使用字符串而不添加任务，也可以仅返回错误，但我想涵盖这两种示例。  

Now when we go down and we start looking at the test cases, let's take adding a task as an example.  
现在让我们开始查看测试用例，以添加任务为例。  

First thing we'll do is clear the tasks, and then we're going to assert if you add Task 1, you expect the list just to have Task 1.  
我们首先会清空任务列表，然后断言添加 Task 1 后，列表中应仅包含 Task 1。  

Once you add Task 2, you expect the list to have Task 1 and Task 2.  
添加 Task 2 后，列表中应包含 Task 1 和 Task 2。  

Once you add Task 3, you expect it to have Task 1, Task 2, Task 3, etc.  
添加 Task 3 后，列表中应包含 Task 1、Task 2 和 Task 3，以此类推。  

But what we wanted to do is then, if we're trying to add an empty task at any point, instead of doing this assert and expecting what the list would look like, we expect an error to come back regardless of what the list looks like.  
但我们想做的是，如果在任何时候尝试添加一个空任务，而不是断言列表的内容，我们期望返回一个错误，而不管列表的状态如何。  

We don't need to clear the list beforehand or anything like that.  
我们不需要事先清空列表或做其他准备。  

Then we just say if we're testing to add an empty task, we want to see if pytest raises that error, a value error.  
然后我们会测试添加空任务，并检查 pytest 是否引发了值错误（ValueError）。  

As we've done here where we see if there's not a task, we're raising the value error "task cannot be empty," and if it raises that when we try to add an empty task as you're seeing here.  
正如我们在此处所做的那样，如果任务为空，我们会引发值错误“任务不能为空”，并在尝试添加空任务时验证它是否正确引发错误。  

Then, similarly, as we've seen before for removing a task.  
接下来，类似地，针对删除任务的情况进行处理。  

For example, we're going to clear the tasks; we'll add three tasks. If we have one, two, and three, and we try to remove two, we expect it to be one and three.  
例如，我们清空任务列表后添加三个任务。如果任务列表是 1、2 和 3，我们尝试删除 2，期望列表变成 1 和 3。  

If we try to remove one, we expect it to be three.  
如果尝试删除 1，期望列表变成 3。  

If we try to remove four, then we're expecting the string "task not found" because of how we've architected it here.  
如果尝试删除 4，期望返回字符串“任务未找到”，因为我们在此架构中定义了这种行为。  

In a real-life application, I would recommend you raise errors in this case instead of just returning a string, but I just wanted to show from testing what it would look like in both scenarios.  
在实际应用中，我建议您在这种情况下引发错误，而不是仅返回字符串，但这里我想通过测试展示两种场景的表现。  

Now once you've done that, and then, of course, you'd expect this to be returned.  
完成后，当然您会期望这些结果被正确返回。  

But at this point, you've added one, two, and three, you've removed one and two, so you would expect to remove three to give you back an empty list.  
但此时，您已经添加了 1、2 和 3，并删除了 1 和 2，因此删除 3 后应该返回一个空列表。  

There's a few other tests in here, list tasks, clear tasks, all of those things. It's worth taking a look at.  
这里还有其他几个测试，例如列出任务、清空任务等，值得一看。  

Now, the other thing just to note, of course, is at the top, I've said this `%%file tasks.py`.  
另一个需要注意的是，我在顶部使用了 `%%file tasks.py`。  

This is a Colab-specific thing, and this Colab-specific thing is to save this out as a file `tasks.py`.  
这是 Colab 特有的功能，用于将代码保存为 `tasks.py` 文件。  

When I run this, what's going to happen is the code isn't actually executing, the code is being saved by Colab as `tasks.py`.  
运行时，代码实际上并未执行，而是被 Colab 保存为 `tasks.py` 文件。  

When I come down to this cell, then I'm going to run pytest with `tasks.py` and we can run that, and we can see that the tests all passed.  
然后我会运行 pytest 测试 `tasks.py`，可以看到所有测试都通过了。  

There's no false positives here, and it looks like it's working the way that we would like it to work.  
这里没有误报，代码看起来运行得很符合预期。  

But the thing that would be good homework for you to do is decide what would you prefer to do here.  
但作为作业，您需要决定更倾向于采取哪种处理方式。  

Do you want to raise an error when something like this happens and then test for that, or do you just want to return status and do nothing and test for that?  
当出现这种情况时，您是希望引发错误然后测试，还是仅返回状态并测试？  

But it would be good to be consistent throughout.  
但无论选择哪种方式，保持一致性是很重要的。  

One of the advantages of using an LLM to help write automated tests is that it will write them in a consistent style.  
使用 LLM 编写自动化测试的优势之一是它会以一致的风格编写测试。  

This can be really helpful for you and your teammates, especially as your codebase grows and new functionalities and their associated tests are added later.  
这对您和团队成员非常有帮助，特别是在代码库不断增长并添加新功能及相关测试的情况下。  

Now, pytest, it's just a single automated testing framework, and a really good one at that.  
Pytest 是一个非常优秀的自动化测试框架，但它只是众多框架之一。  

But of course, if you want to try a different framework, or if you're working in a different programming language, please go ahead and experiment with them.  
当然，如果您想尝试其他框架或使用不同的编程语言，请随时进行尝试。  

For example, if I ask the LLM to convert my Python to-do list code into JavaScript, it'll happily do so.  
例如，如果我让 LLM 将我的 Python 待办事项代码转换为 JavaScript，它会很乐意完成。  

Then you could ask for suggestions on automated testing libraries for JavaScript and have it write some tests for you with those.  
然后，您可以询问 JavaScript 的自动化测试库建议，并让它使用这些库为您编写测试。  

When I tried this, it went ahead and suggested the Jest framework, and it then wrote this code.  
当我尝试时，它推荐了 Jest 框架，并编写了相关代码。  

The important thing here, regardless of the language that you're working in, is that with a good understanding of what your code does, you can guide an LLM to do the exhaustive part of the work for you.  
这里重要的一点是，无论使用哪种语言，只要您对代码的功能有很好的理解，就可以指导 LLM 为您完成繁琐的部分工作。  

It can help you generate test cases.  
它可以帮助您生成测试用例。  

It can write the scripts or an automated testing framework like pytest or Jest, and so much more.  
它可以编写脚本或使用自动化测试框架（如 pytest 或 Jest），还有许多其他功能。  

Now, so far, you've just been testing that your code functions, but does it function well, meaning quickly, with good user experience, and under conditions of high traffic or other stresses?  
到目前为止，您只是测试了代码的功能性，但它运行得好不好呢？是否快速、具备良好的用户体验，并能够应对高流量或其他压力条件？  

That will bring us to the next phase of testing: performance testing.  
这将引导我们进入测试的下一阶段：性能测试。  

Let's go on to the next video to take a look.  
让我们进入下一个视频了解更多。  

To begin developing a high-level sense of how an LLM can help you think through testing strategies, let's begin with a basic Python example.  
为了初步了解大语言模型（LLM）如何帮助您构思测试策略，让我们从一个简单的 Python 示例开始。  

It's a Flask app with a web API.  
这是一个带有 Web API 的 Flask 应用程序。  

Flask, if you're not familiar with it, is a lightweight web framework for Python, and it's perfect for our demonstration.  
如果您不熟悉 Flask，它是一个轻量级的 Python Web 框架，非常适合我们的演示。  

Let's walk through the code and we'll take a close look at how it works.  
让我们一起查看代码，并仔细了解它是如何工作的。  

This app has a single endpoint `/API/greet/name`, and this will take a name as a parameter and return a greeting message.  
这个应用程序只有一个端点 `/API/greet/name`，它接受一个名字作为参数并返回一条问候消息。  

If you're running it in a shared environment like Colab, you have to change it a little to use threading.  
如果您在像 Colab 这样的共享环境中运行它，您需要稍作修改以使用多线程。  

Notebooks like Jupyter or Colab will always finish the code in the current cell before they move on to the next one.  
Jupyter 或 Colab 之类的笔记本会在完成当前单元格的代码后再进入下一个单元格。  

If you want to launch a server with an API that you're going to call, like we're going to be doing here, it does need to run in a separate thread, and that will let you get on with the rest of your notebook.  
如果您想启动一个带有 API 的服务器以供调用（就像我们在这里要做的那样），它需要在一个单独的线程中运行，这样您就可以继续使用笔记本中的其他部分。  

You probably would not want to do this in a production environment, but for learning purposes with a notebook, it's perfectly okay.  
在生产环境中您可能不想这么做，但在学习环境下使用笔记本是完全可以接受的。  

Once you have a running API, if it's on your server, you can call it with cURL, or if you want to use Python, you can use requests like this.  
一旦 API 运行起来，如果它在您的服务器上，您可以使用 cURL 调用，或者如果您想用 Python，可以像这样使用 requests。  

This will be the IP address of your server.  
这里将是您服务器的 IP 地址。  

If you're running it in Colab with the threading code, Colab will report back to you the address of the server.  
如果您在 Colab 中使用多线程代码运行它，Colab 会将服务器地址反馈给您。  

Make sure you use the one that's reported back to you instead of the address that's in the slides.  
确保使用报告回来的地址，而不是幻灯片中的地址。  

Now that you have your example up and running, pause the video and think about what test cases you might want to use for your API.  
现在，您的示例已经运行起来了，请暂停视频并思考您可能为 API 设计的测试用例。  

What data might you pass in to check if it's behaving properly, and how would you break it?  
您可能会传入哪些数据以检查它是否正常运行，以及您会如何破坏它？  

#### Practice

Setup the Flask app code provided in the downloads for this video, either in the Coursera lab environment provided at the start of the module, in Google Colab (use the notebook provided), or on your own computer (use the flask_app.py script).  
设置本视频下载中提供的 Flask 应用代码，可以在模块开头提供的 Coursera 实验环境中运行，也可以在 Google Colab 中运行（使用提供的笔记本），或者在您自己的计算机上运行（使用 flask_app.py 脚本）。  

Once you have the app up and running, think through the test cases you might want to consider to check that the app functions as expected.  
一旦应用程序启动并运行，请思考您可能会考虑的测试用例，以检查应用程序是否按预期运行。  

Try writing code to test the usage of the app for the cases you come up with.  
尝试为您想出的用例编写代码来测试应用程序的使用。  

You don’t need to write full tests at this point, simple test use cases are enough to get started.  
此时您不需要编写完整的测试，简单的测试用例就足够开始了。  

Next, ask an LLM to analyze the Flask app code and come up with a set of test cases to check how the app functions.  
接下来，请使用 LLM 分析 Flask 应用代码，并提出一组测试用例来检查应用程序的功能。  

Compare the output of the model to your own list of ideas.  
将模型的输出与您自己的想法列表进行比较。  

When you are done, come back to see how Laurence carried out this conversation.  
完成后，回来查看 Laurence 是如何进行此对话的。  

---

#### 2
Hopefully, you came up with a few ideas.  
希望您已经有了一些想法。  

Now I'd like you to try using GPT or another LLM as your testing partner and see what it comes up with.  
现在我希望您尝试使用 GPT 或其他 LLM 作为测试伙伴，看看它会生成什么。  

In the last course, you practiced using a set of prompting best practices to guide the LLM to the output that you wanted.  
在上一课中，您练习了一组提示最佳实践，以指导 LLM 生成您想要的输出。  

Here's a quick recap.  
以下是快速回顾。  

You should always be specific in your prompts and provide details and context about your problem.  
您应该始终在提示中具体说明问题，并提供详细信息和上下文。  

Assigning a role can help the model tailor the output that you receive.  
分配角色可以帮助模型调整生成的输出内容。  

Taking that a step further by asking the model to behave as an expert and critique your work can help you get really specific well-formatted output.  
进一步要求模型作为专家提供反馈，可以帮助您获得特别具体且格式良好的输出。  

Then last, bringing your own expertise into the mix and having that back and forth with the model can help you steer the LLM to write the exact code that you want and need.  
最后，将您的专业知识与模型结合，通过互动帮助您引导 LLM 编写所需的精确代码。  

With these best practices in mind, here's an example prompt that can help you think through testing strategies for that simple web app.  
牢记这些最佳实践，以下是一个帮助您思考该简单 Web 应用测试策略的提示示例。  

As an expert software tester who's teaching a new person how to write test cases, can you please analyze this code and provide a set of test cases explaining each one?  
作为一名正在教新人编写测试用例的软件测试专家，请您分析这段代码并提供一组测试用例，同时解释每个用例。  

Here's what I got when I used this prompt with GPT.  
以下是我用 GPT 输入此提示时得到的内容。  

Remember, LLMs are probabilistic in nature, so the exact output that you'll get will depend on a number of factors such as changing random seeds or indeed the model version that you're using.  
请记住，LLM 的本质是概率性的，因此您得到的具体输出会受到诸多因素的影响，例如随机种子的变化或您所使用的模型版本。  

It takes a look at my code, it analyzes my code, understands it defines what it's doing, but more importantly, it gives me the test cases.  
它查看了我的代码，分析并理解了代码的功能，但更重要的是，它给出了测试用例。  

The first, of course, is the basic greeting.  
第一个用例当然是基本的问候功能。  

The basic greeting is `/API/greet something`, and the expected output will be a JSON message, "Hello, something."  
基本的问候是 `/API/greet something`，预期输出是一个 JSON 消息：“Hello, something”。  

The second test case then would be URL encoding handling.  
第二个测试用例是 URL 编码处理。  

So if I passed in a string that has a space in it, for example, "John Doe," it would be `%20` as the URL encoding of that space, but I expect my output not to have the URL encoding, and it would just say, "Hello, John Doe."  
例如，如果我传入的字符串中包含空格，比如“John Doe”，空格会被编码为 `%20`，但我期望输出中不包含 URL 编码，而是直接显示“Hello, John Doe”。  

The model goes on to suggest several other test cases like special characters, empty names, numeric input, and so on.  
模型继续建议了其他几个测试用例，例如特殊字符、空名字、数字输入等。  

All of these are important corner cases to consider and test for.  
所有这些都是需要考虑和测试的重要边界情况。  

Scrolling to the bottom of the response, you can see the model also included implementations of each of these test cases.  
滚动到响应底部，您会发现模型还包含了每个测试用例的实现。  

Now, the product you used to write tests here was pretty generic.  
在这里用来编写测试的提示是非常通用的。  

You didn't specify any particular testing strategy, for example.  
例如，您并未指定任何特定的测试策略。  

The tests the LLM suggested here mainly looked at functionality, and they're pretty representative of the type of manual exploratory testing that you might do during early-stage development.  
LLM 在此建议的测试主要关注功能性，非常典型地代表了您在早期开发阶段可能进行的手动探索性测试。  

Let's now move on to the next video to take a more detailed look at exploratory testing, and in particular, how you can use an LLM to help you and your colleagues in that process.  
让我们进入下一个视频，更详细地了解探索性测试，特别是如何使用 LLM 帮助您和您的同事完成这一过程。  

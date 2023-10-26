---
title: ChiPy Speak Script
date: 2023-10-26 17:16:41
tags:
	- Speak
---

### Preface

It’s been a while since the last time I wrote a blog. I have been doing a lot of travels in the last couple months.

On December 14th I will have the pleasure of presenting my first public tech speak at the Chicago Python User Group. [Here](https://www.chipy.org/meetings/238/) is a link to the event with some description of my speak. So I’d like to use this blog as a place to write down the script of my speak so that I could keep practicing.

<!-- more -->

### Intro

Good evening. First of all I’d like to thank the Chicago Python User Group for obviously giving me this great opportunity to present in front of you all. My name is Jinge Li and today I’d like to talk about an open source project that I have been working on for the last three years. It is a Python library named PyPDFForm.

Here is a quick agenda for this speak. I’d like to spend the first 20 to 25 minutes talking about some backgrounds regarding this project. What are some of my personal tech journeys? What sparked this idea? And just general motivations and stuff. We will spend the next 10-15 minutes going through a small coding session where I will showcase some simple but essential functionalities of the library. And finally we will wrap up with some discussions about the future and Q and A. OK?

### Background

So obviously you all are here to attend the **Chicago** Python User Group. And we can’t talk about background without talking about some background of Python. And I’m sure we all agree Python is in a great state right now.

It has stayed at the top of the TIOBE Index for many years. As a matter of fact I don’t recall when was the last time it dropped out of the top five.

On top of that it was three-time language of the year in the last five years. In the year of 2018, 2020, and 2021 Python is the language with the most popularity.

And as a general purpose language it has a large variety of usages across different areas. Here on the right we have two most outstanding ones, web development and data science. Devops also uses it to quickly script stuff. It’s also used a lot for serverless stuff such as AWS lambda.

It is loved by startups. Many startups need to spin up their service prototypes rapidly. This is where Python shines, it can develop things very quickly.

And finally it’s even used by non-developers to automate daily tasks. My girlfriend, for example, is an accountant. And the other day she came to me and was like could you teach me a bit of Python. Because she needed to bulk process some Excel sheets. So overall I’d say we Python developers are currently living in a good world.

Now that we know what a great tool Python is, it’s meant to be used to solve problems. And in the world of software engineering, it doesn't matter what languages or tech stacks, one of the outstanding problems is PDF generation. And here on the right you can see why.

But jokes aside, PDF is something that suits almost any business model’s needs. Ecommerce business generates invoices or receipts. Law firm generates legal documents. And there are many more examples you can think about in other industries.

It is compressed, consistent, cross platform, and user friendly. A PDF file can be viewed on pretty much any machine nowadays. From your browser chrome to something more professional like Adobe Acrobat they all support PDFs. It has become a standard.

So now we know that PDF generation is a problem, we need a solution to it. And in the world of Python there is a great solution.

It is a Python library called reportlab. I’m not sure how many of you have heard of it. In essence reportlab describes PDF layouts using a markup styled syntax named RML. Now obviously the Python library abstracts these markup tags into different Python objects.

But with this library you can create complex layouts like grids or tables.

And it ultimately archives PDF generation in a programmatic way using Python code.

Now however, and yes there is always the however.

It is one thing if you are trying to generate something like this. You know. You have a title at the top. The main section is trisected vertically. Each section has some simple texts. Nice and easy.

But it’s another thing if you are to, say, generate something that looks like this. Here you have tens of rows where each row’s cells don’t align with one another. Images that are squeezed into some cells. I don’t even want to talk about texts that are vertically aligned. Yikes.

So what does this tell us? Well, PDFs can be complex. I think we all agree this one on the right is complex and trust me this is not uncommon.

And for a PDF as complex as this, the reportlab code that’s used to generate this is messy. It is lengthy and can very quickly become unmaintainable.

And it’s just not very modern to implement such complex layouts using markup syntax. This is why in the world of frontend we invented React and Vue. Ask yourself when was the last time you wrote vanilla HTML when building web apps.

So now that we have learned some challenges when it comes to generating PDFs using reportlab, let’s shift the gear a little bit and I’d like to spend some time talking about myself for a bit.

When I first graduated from college, my first job was at this local startup here in Chicago. What they are is they are a third party software solution provider to government’s day to day tasks, more specifically the law enforcement department. I will give you an example of what they do. If let’s say you are driving in the northern side of Illinois, like in Lake County, and you are a little too heavy on your gas pedal and got pulled over by an officer and received a speeding ticket, there’s a chance that the speeding ticket is from where I worked.

So now with that being said, any of you who have ever worked with the government will know one thing that’s true. They have a lot of paperwork. And that complex PDF I just showed you earlier is actually very close to some of the documents we have to generate for our clients. And the struggles I was talking about when using reportlab were the exact same struggles I had at work.

So I started thinking about how I can improve this process, and this is when I started doing my research. Well the first thing that came to my mind is PDF forms. I’m sure many of you here have dealt with it at some point of your life. Like it used to be that when you go file your taxes those forms you downloaded and filled were PDF forms. When you apply for your U.S. passport the application you filled in was also a PDF form. So the moment I thought about that I was like, great I just need to prepare the PDF I want to generate into a form and fill it programmatically with the data that needs to be plugged in.

And in the world of software development, one thing that’s almost always true is that we shouldn’t be reinventing wheels. And that’s why I ask myself, is there an existing solution already? Right? There’s no way I’m the only person who ran into this problem and there’s gotta be something implemented already.

But it turned out the answer was no, and I was shocked because that’s a very rare answer to that question in our world. Ok it’s not that there’s no existing solutions. It turned out that existing Python libraries that do similar things require some non-Python dependencies. Some of them are at the system level. Other ones may require some other binaries in another language bundled together. And that’s not what I wanted.

And just like how many other open source projects were started, I didn’t like any of the existing solutions and that’s when I decided to write my own. Now the first question I ask myself is what data structure should I use to represent a PDF form. So with PDF forms the widgets on there can be tagged with a name right? Now I just need to pair the name of the widgets with their values. It is better to be something built in. This is quite obvious right, anyone?

A dictionary that’s right. And this is the start of PyPDFForm, or I should say at the time it was only a script I wrote. What it does in its essence is exactly what I just said, it fills a PDF form from a Python dictionary.

Now I did not implement it from scratch. It does have some dependencies but PyPDFForm and all its dependencies are pure Python.

It also has some other miscellaneous functionalities such as drawing images and merging multiple PDFs together, you know, just some nice to have stuff.

Now let me spend a bit time talking about this last bullet point, what do I mean by that? Well the previous process of generating PDF forms would be that your clients give you a PDF that they want you to generate, and it is on you, the developer, to write the script that would precisely describe the layout of it. This process is just very tedious and time consuming. Well now instead of you scripting out the layout, the layout is already there because when your clients hand you the PDF, your project manager can just go ahead and turn it into a PDF form using any main steam form preparation tool like Adobe Acrobat. All you have to do is figuring out what data needs to go on there, preparing the dictionary and plugging it in. This is a much less painful process for developers and draws clear scope for the process of PDF generation.

Before we move on, any question?

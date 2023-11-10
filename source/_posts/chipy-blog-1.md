---
title: ChiPy Speak Script
date: 2023-11-06 22:16:41
tags:
	- Speak
---

### Preface

It’s been a while since the last time I wrote a blog. I have been doing a lot of travels in the last couple months.

On December 14th I will have the pleasure of presenting my first public tech speak at the Chicago Python User Group. [Here](https://www.chipy.org/meetings/238/) is a link to the event with some description of my speak. So I’d like to use this blog as a place to write down the script of my speak so that I could keep practicing.

<!-- more -->

### Intro

Good evening. First of all I’d like to thank the Chicago Python User Group for obviously giving me this great opportunity to present in front of you all. My name is Jinge Li and today I’d like to talk about an open source project that I have been working on for the last three years. It is a Python library named PyPDFForm.

Here is a quick agenda for this speak. I’d like to spend the first 20 to 25 minutes talking about some backgrounds regarding this project. What are some of my personal tech journeys? What sparked this idea? And just general motivations and stuff. We will spend the next 10-15 minutes going through a small coding session where I will showcase some simple but essential functionalities of the library. And finally we will wrap up with some restrictions and the future of the library and Q and A. OK?

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

And it ultimately achieves PDF generation in a programmatic way using Python code.

Now however, and yes there is always the however.

It is one thing if you are trying to generate something like this. You know. You have a title at the top. The main section is trisected vertically. Each section has some simple texts. Nice and easy.

But it’s another thing if you are to, say, generate something that looks like this. Here you have tens of rows where each row’s cells don’t align with one another. Images that are squeezed into some cells. I don’t even want to talk about texts that are vertically aligned. Yuck.

So what does this tell us? Well, PDFs can be complex. I think we all agree this one on the right is complex and trust me this is not uncommon.

And for a PDF as complex as this, the reportlab code that’s used to generate this is messy. It is lengthy and can very quickly become unmaintainable.

And it’s just not very modern to implement such complex layouts using markup syntax. This is why in the world of frontend we invented React and Vue. Ask yourself when was the last time you wrote vanilla HTML when building web apps.

So now that we have learned some challenges when it comes to generating PDFs using reportlab, let’s shift the gear a little bit and I’d like to spend some time talking about myself for a bit.

When I first graduated from college, my first job was at this local startup here in Chicago. What they are is they are a third party software solution provider to government’s day to day tasks, more specifically the law enforcement department. I will give you an example of what they do. If let’s say you are driving in the northern side of Illinois, like in Lake County, and you are a little too heavy on your gas pedal and got pulled over by an officer and received a speeding ticket, there’s a chance that the speeding ticket is from where I worked.

So now with that being said, any of you who have ever worked with the government will know one thing that’s true. They have a lot of paperwork. And that complex PDF I just showed you earlier is actually very close to some of the documents we have to generate for our clients. And the struggles I was talking about when using reportlab were the exact same struggles I had at work.

So I started thinking about how I can improve this process, and this is when I started doing my research. And the thing that came to my mind is PDF forms. I’m sure many of you here have dealt with it at some point of your life. Like it used to be that when you go file your taxes those forms you downloaded and filled were PDF forms. When you apply for your U.S. passport the application you filled in was also a PDF form. So the moment I thought about that I was like, great I just need to prepare the PDF I want to generate into a form and fill it programmatically with the data that needs to be plugged in.

And in the world of software development, one thing that’s almost always true is that we shouldn’t be reinventing wheels. And that’s why I ask myself, is there an existing solution already? Right? There’s no way I’m the only person who ran into this problem and there’s gotta be something implemented already.

But it turned out the answer was no, and I was shocked because that’s a very rare answer to that question in our world. Ok it’s not that there’s no existing solutions. It turned out that existing Python libraries that do similar things require some non-Python dependencies. Some of them are at the system level. Other ones may require some other binaries in another language bundled together. And that’s not what I wanted.

And just like how many other open source projects were started, I didn’t like any of the existing solutions and that’s when I decided to write my own. Now the first question I ask myself is what data structure should I use to represent a PDF form. So with PDF forms the widgets on there can be tagged with a name right? Now I just need to pair the name of the widgets with their values. It is better to be something built in. This is quite obvious right, anyone?

A dictionary that’s right. And this is the start of PyPDFForm, or I should say at the time it was only a script I wrote. What it does in its essence is exactly what I just said, it fills a PDF form from a Python dictionary.

Now I did not implement it from scratch. It does have some dependencies but PyPDFForm and all its dependencies are pure Python.

It also has some other miscellaneous functionalities such as drawing images and merging multiple PDFs together, you know, just some nice to have stuff.

Now let me spend a bit time talking about this last bullet point, what do I mean by that? Well the previous process of generating PDF forms would be that your clients give you a PDF that they want you to generate, and it is on you, the developer, to write the script that would precisely describe the layout of it. This process is just very tedious and time consuming. Well now instead of you scripting out the layout, the layout is already there because when your clients hand you the PDF, your project manager can just go ahead and turn it into a PDF form using any main steam form preparation tool like Adobe Acrobat. All you have to do is figuring out what data needs to go on there, preparing the dictionary and plugging it in. This is a much less painful process for developers and draws clear scope for the process of PDF generation.

Before we move on, any question?

### Coding Session

So obviously talk is cheap. Let's spend the next ten fifteen minutes on a coding session to show you guys some of the stuffs the library can do.

So right here I have an empty directory on my computer. Let's start by first creating a virtual environment.

```shell
python3 -m venv venv
source venv/bin/activate
```

The installation of PyPDFForm is similar to any other libraries. You just do the normal pip install.

```shell
pip install PyPDFForm
```

So I could show you how to prepare a PDF form from scratch but we only have that much time and there are many other tutorials online for many tools. So I will skip it and [here](https://eforms.state.gov/Forms/ds11.pdf) I have a random PDF form I found online. It's an application for the U.S. passport. Let's use this for our demo. So let's download it and put it in our directory.

And we can instantiate a PyPDFForm object using the form we just downloaded.

```python
from PyPDFForm import PyPDFForm

pdf = PyPDFForm('ds11.pdf')
```

Now the first thing you want to ask yourself when you get a PDF form is what are the names for all these widgets or elements, aka what are the keys of the dictionary you will fill it with. So here I wanna show you a somewhat new and experimental functionality I developed recently called preview.

So let's create an output file and then write the preview of the form into it and see what happens.

```python
with open('output.pdf', 'wb+') as f:
    f.write(pdf.preview)
```

And if we go ahead and open up the output PDF, we will see that each element will have its name displayed on top of it in red.

So this does look better on a simpler PDF form. But as you can see with this one it gets quite messy when it's complex, which is why it's an experimental feature and I'm still thinking about how I can improve it.

A more mature method to inspect a form is the generate schema method. So you just have to do this:

```python
from pprint import pprint

pprint(pdf.generate_schema())
```

And what you are seeing here is a JSON schema that describes the JSON object, or in the context of Python the dictionary that the object expects. So for example `Applicant First Name` takes a string and has a maximum length of 17. `Applicant Changing Gender` is a boolean value which is saying it is a checkbox. `Card Status` takes an integer type and has a maximum value of 3 and why is that? Because it's a radio button and has 4 different choices.

Combining the schema and the preview will give you a pretty good idea on what data should go into the form. And another nice thing is when you do have your dictionary ready, you can use the schema to validate the dictionary just like how you would use your JSON schema to validate a JSON object.

So now that we know what data needs to go into the object, let's fill it out. As you can see from the schema, none of these elements are required so let's just fill the three elements we just discussed. And all you have to do is calling the fill method and pass the dictionary to it.

```python
filled = pdf.fill(
    {
        "Applicant First Name": "Jinge",
        "Applicant Changing Gender": True,
        "Card Status": 1,
    }
)
```

And now you have your filled form, the object implements itself similar to a file object. So you can simply write it out like this:

```python
with open('output.pdf', 'wb+') as f:
    f.write(filled.read())
```

And if we open up the output file, we will see our first filled PDF form.

So one thing you will notice is that the library does respect the styles of these elements. So if we look at this first name field you can see how each character is evenly spaced out. This is actually a property for these text fields called comb that you can set when you create the form and what's nice about PyPDForm is that it's smart enough to know the styling and adjust accordingly. And I will show you another example in just a minute.

So let's move away from the code and try to tweak our PDF form for a bit. And there are many tools out there that you can use to prepare or modify PDF forms. The most professional one is probably Adobe Acrobat. The one I'm going to use here is a web based one called DocFly. So let's upload our PDF form and make some changes to it.

As you can see here, this first name text field did have the combed property set and that's why its characters are evenly spaced out. If I deselect the property you can see the text no longer do that.

Let's look at another one. On this next page you have this other name field called `Name of Applicant 2`. What I'm going to do is to change the style of texts that are filled into it. So let's first change the font from `Helvetica` to `Times New Roman`. And then I think the texts are just too big even though they are not so I'm changing the font size from 18 to 12. I'm also changing the font color to, let's say magenta. I'm making it both bold and italic. And finally I'm making it align to the middle instead of to the left.

That seems to me enough changes. Let's save the file and download it. And I'm making no other code changes besides changing which template to use and adding that new text field we just made a lot of changes to to the dictionary.

```python
pdf = PyPDFForm('ds11-copy.pdf')

filled = pdf.fill(
    {
        "Applicant First Name": "Jinge",
        "Applicant Changing Gender": True,
        "Card Status": 1,
        "Name of Applicant 2": "Jinge",
    }
)
```

And if we run it, you will see now that the name field on the first page is no longer evenly spaced out, and the name field on the second page now has a different font with a smaller font size and color. It's bold and italic and align to the middle. This just shows how smart the library is. If you use is and need to make styling changes, have your project manager do it because they should be experts at Adobe Acrobat and all you need to focus on is the data that needs to go in there.

Well then you may be wondering, sometimes the style of the template is not what it should be, but at the same time I don't have one of these form preparation tools to change it. Well the PyPDFForm object does let you to tweak some of the styles during run time. Let's look at how it works.

Let's say now that we have made this first name field no longer spaced out, I feel like its font size should be larger. And the way you access all of these elements of your object is through the elements attribute. And just like how you would access a value of dictionary through its key, you do the same thing right here. And here you can set its font size by just doing this:

```python
pdf.elements["Applicant First Name"].font_size = 30
```

And if we re-run our scripts, you will see that you can change the font size during run time if you don't like it.

Same thing, so let's say you regret making the second name field's font so small and you no longer like magenta as its font color. You can make the same changes for it too.

```python
pdf.elements["Name of Applicant 2"].font_size = 18
pdf.elements["Name of Applicant 2"].font_color = (1, 0, 0)
```

Here for the font color it takes an RGB tuple, let's make it red. Re-run the script and let's see the effect.

And finally you say forget everything I just want to make every single text I filled into the PDF form super large and blue. Well it turns out you can do that too when you instantiate the object.

```python
pdf = PyPDFForm('ds11-copy.pdf', global_font_size=50, global_font_color=(0, 0, 1))
```

Obviously these are just the peak of iceberg. There are some other functionalities like draw text, draw images, and merge multiple PDFs together. But I really want to show the essential part of it, which is the actually filling piece.

Any question before we move on?

### Conclusion

I’d like to wrap up this speak with some discussions around restrictions and future improvements that are planned. Because many of you may be wondering, now that you have shown what the library can do, what can it not do?

Well the library requires you to have a static PDF form template as a baseline, so the largest restriction with it is that it cannot generate dynamic sections. So on the right you see a pretty common example of an invoice PDF. Notice that middle section where all the items are listed? That’s not something you can handle with the library. I mean sure maybe you can have like ten rows of text fields and it will probably work for the most part. But the point I’m trying to make is that it's not flexible. So all and all for PDFs with dynamic sections you still need something like reportlab.

The next thing is that the library only supports some of the most common elements like you just saw in the demo. Now the elements that you guys saw probably cover 90% of the usage of PDF forms. But still there are more. I can give you two common ones. Image fields, you know, the one where you can click on it and attach an image on it. Another one is signature fields, kinda similar to image fields but instead where you sign.

And finally like what I said earlier in the demo, there are many PDF form preparation tools out there. Some of them generate the form the same way but some other ones are different under the hood. I believe I have made the library to support most of the mainstream ones out there but still there is no way I have explored every single one of them out there.

With that being said, let’s talk about some future improvements that are currently on my radar for the library.

First, obviously I’d love to support more elements. Using image fields for example, I tried to support it about two years ago but was not able to. But at the time I was also not as experienced in terms of developing this library as I am nowadays, so I have been having the thoughts of picking it back up again.

Next I would love to support more of those unexplored form preparation tools out there. This in fact is something I wrote on the README. If you ever run into a problem where whatever tools you are using to prepare the PDF form that doesn’t work with the library, open an issue and I will try to get it supported.

And you tell me! Ya that’s correct. And this brings me back to why I’m here to present in front of you all. Recently I have run into kinda a stale state when working on PyPDFForm where I’m starting to run out of ideas on what features to bring next. This is why I came here, to present in front of a group of public, and hopefully by speaking with you guys some new ideas will spark again. And this doesn’t have to happen immediately. If any of you find this library useful, or simply find it interesting and try play with it for a bit, I’m always a believer that users are the best source of ideas.

Any other question?

Well thank you very much. It is my honor to speak in front of you all and again thanks to Chicago Python User Group for having me.

---
layout: default
image: /assets/images/hackers-1.jpg
---


## Project Proposal/Outline

Guidelines:

- Your project must be written (primarily) in Python.
- The project proposal must be approved by the Instructors

Due date and expectations:
- Your proposal will be graded on all of the components based on their
state by the end of the day on **3/27/2021**. 
Your expected progress on the project code/pseudocode at this point will
vary among students depending on your prior experience.


### Getting started
Assuming that your mini-project will be the springboard for your final
project you can begin to create you can begin by changing the name of 
your `mini-project` repo to a new name representing what you want your 
project to be called (if you haven't already done so). This can be done 
from the settings page of the repo on GitHub.

Once you have changed the name of your repo you can now clone it to your
laptop, or if you have already done so, you can continue to use your existing
clone (it can handle keeping up with the name change). If you have not already
done so, you can now add the following files and folders to create your starting project file structure, with all files and folders renamed as you would like. 

```
project/
├── src/
│   ├── __init__.py
│   └── module.py
├── README.md
└── setup.py
```

### Proposal
Your project repo currently has your mini-project proposal written in the 
README.md file. Create a copy of this file called `proposal.md`, as a starting
point for your official project proposal. The `proposal.md` file in the root
of your project repo will be the file we will reference for evaluating
your proposal.

In this proposal you should expand upon the contents in your mini-project
proposal to incorporate any feedback that we provided previously, and to update it
with any new ideas or progress you have made in designing your project.
Using markdown, you should create nicely formatted headings and paragraphs
to list the following topics and your answers:

- What task/goal will the project accomplish and why is this useful?

This should be a concise statement that would convince a user that your
program is worth their time to read more about and try using.

- What type of data/input will a user provide to the program?

This will vary depending on the strutcure of your program. If it is a game
the user may only provide keystrokes or screentouches; if you made a CLI
program the user may only provide options to toggle; if you made a webapp
the user may use their mouse and keyboard to toggle input options in a web
page; if you made a program that takes data as input then the user may 
need to enter a CSV or JSON or other type of data file as an option.

- Where will the data come from?

Almost every program will involve *some* type of data. This data may be 
provided as input by the user, or it may be generated by your program in 
response to the user inputs, or it may be accessed from a database that
your distribute inside of your program (e.g., CSV file) or from an online
database that is access using a REST API. Describe it and show an example
of the format, like below.

```
species    latitude    longitude    color
A    30.0    100.0    red
A    31.0    101.0    blue
B    29.0    105.2    red
B    29.5    101.2    red
...
```
And if it is from a REST API then describe the API options, provide a link, 
explain which paths of the API you will access, and any rules or limits you've
found about how it can be accessed.

- How will a user interact with the program?

If you are developing a CLI or API then write a mock example like below. If
you are writing any other kind of input, describe which options a user might
be able to toggle. 

```
# mock example of command line options to a program
myprogram --latitude-min 90 --latitude-max 110 --avg-color
```

- What type of output will the program produce (e.g., text, plots)? 

Describe the format of these outputs, show an example of what you have 
in mind, even if you have to draw it by hand. Think about it, is this the
most useful way for the user to get the output? Would it be more convenient
to return the result to STDOUT, or to a file, or to a webpage?

- What other tools currently exist to do this task, or something similar?

Do some research. Do some google searching. What other programs currently
exist to do this thing. Provide links to them. Describe how your program
will be different. 


### Psuedo-code and/or code
You should begin to write properly formatted psuedo-code to layout the 
design of your program within your text editor. This means that you should
organize code properly in the module (e.g., shebang, imports, docstrings, classes)
and write classes or functions with docstrings and comments. 
Begin to describe the major tasks using code. This can be 
contained in one or more modules. Once you have these major classes defined
you can begin to work on the first one, and work towards creating a minimal
working example. Once you have this minimal working example it will be easier
for others to collaborate on your code with you.


### Update your README.md

- Write the name of your program as a level-1 header
- Copy your answer about what task/goal your project is intended to accomplish
and enter it below the header as a text.
- Write a level-3 header called "in development"
- Write a paragraph below this describing how developers can install the 
program locally to help work on the code. This should include instructions
like the following:

```
conda install [list dependencies here...] -c conda-forge ...

git clone [myproject-link]
cd ./myproject-name
pip install -e .
```

Test to make sure your code is installable, even if the Python 
modules are mostly empty for now.


### Goal
In the following weeks we will begin to engage in *collaborative* coding, 
where you will fork each others' repos, try out the code, and try to contribute
to it by making edits. This will be greatly facilitated by a well-written 
proposal that describes the goal of the software, and the intended design of
it. As you progress and the code becomes more complex, it may become useful
to develop further details/descriptions of the code to aid other developers
in understanding the structure of your code. We will talk more about this 
in a later session.


### Make your project known

Navigate to the following page on GitHub 
<a href="https://github.com/eaton-lab/hack-the-planet/blob/master/docs/data/usernames.csv">
https://github.com/eaton-lab/hack-the-planet/blob/master/docs/data/usernames.csv</a>
where the course website is hosted
and click on the 'pen' icon to fork and edit the file. Next to your username
where it currently says TBD enter the new name of your project repository
(be sure to enter the correct lower vs upper case letters). Commit your change
and make a pull request. Once we accept the pull request a link to your repo
will appear on the course website under the repos link.

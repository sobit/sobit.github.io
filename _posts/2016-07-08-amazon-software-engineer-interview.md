---
layout:      post
comments:    true
title:       Amazon software engineer interview
description: >
    Personal experience on being hired as a software development engineer at Amazon. Detailed interview process,
    preparation tips, and more.
---

![Amazon - We Pioneer](/assets/amazon-we-pioneer.jpg)

I was recently contacted by a technical recruiter from Amazon. The company was hosting an interview event for software
engineers to join a team in their Berlin office.

The whole process from being contacted to signing the contract took two months. I would like to share my experience on
how it went in general as well as what I believe helped me pass it successfully.

If I failed to mention something important in this article, feel free to start a discussion in the comments section.
There I will try to be as detailed as possible.

<!--more-->


April 27: First contact
-----------------------

I was contacted by the recruiter via [LinkedIn]. She told me they were looking for software engineers to join a team
in their Berlin office and asked me to send her an updated resume if it sounded interesting for me. I always tend to
keep my resume updated, so the next day I sent her an email with it attached.

She responded with some general information about the role and the interview process. The first step was to conduct a
technical exercise via [Hackerrank], which I received a link to separately on the same day.

The exercise was limited to 120 minutes and the recruiter requested that I finish it before May 5th. I decided not to
rush and waited for the upcoming weekend.

[LinkedIn]: https://www.linkedin.com/
[Hackerrank]: https://www.hackerrank.com/


May 1: Prescreening
-------------------

Hackerrank has its own interview platform called [Hackerrank for Work]. That was the tool I landed on when I clicked on
the link in the email. It has a built-in timer, a web editor with some sort of autocompletion for Java, problem
statements and the ability to try your solution with various test cases including your own.

It was never communicated which languages the coding test would be limited to before I started it. Those I could choose
from were C, C++, Java and a couple of others, which ruined my plans to use [Go] or [PHP] - the languages I was the most
proficient in. So I ended up choosing [Java].

The test consisted of three problems which could technically be solved in no particular order.

[Hackerrank for Work]: https://www.hackerrank.com/work
[Go]: https://golang.org/
[PHP]: http://php.net/
[Java]: https://www.oracle.com/java/index.html


### Problems

The first problem was related to an object-oriented design. I was provided with a few classes and their methods'
definitions to solve the problem in the most efficient way while maintaining clean, readable code.

The second problem was an algorithmic one. Here I will give you some advice which helped me personally: *before you
start thinking about which data structures and algorithms to apply for a particular problem, solve the problem manually
and visualize the solution - that will help you get wider picture*. I did it on paper, realized how easy it was, and
transferred my solution into the code.

However, a mistake I made was trying to further optimize it and make the code as beautiful as possible. I already had
all the test cases passing and should have instead used the remaining time to finish the last problem. Bad
prioritization. Lesson learned.

The third and the last problem was about analyzing complexity for the solution given in the previous problem. I was
supposed to explain it as well as justify why I thought it was best from my point of view. However, I covered only the
main aspects due to the lack of time.


May 4: Phone screening
----------------------

The day after I received an email from the recruiter congratulating me on passing the technical test. She asked about
my availability for the week to schedule a phone call and review my technical skills before she could invite me to the
on-site interview. We agreed on May 4th.


### Brushup

I only had two days so I brushed up on the essentials in algorithms and data structures. Specifically, I focused on the
following:

- Sorting: [bubble sort], [quicksort], [merge sort]
- Search: [linear search], [binary search]
- Data structures: [linked list], [hash table], [array], [tree], [binary search tree], [stack], [queue]

Of course, *you need to be able to argue about the complexity of algorithms and common operations on data structures*.
I personally found [Wikipedia] to be a great resource for this kind of analysis.

[bubble sort]: https://en.wikipedia.org/wiki/Bubble_sort
[quicksort]: https://en.wikipedia.org/wiki/Quicksort
[merge sort]: https://en.wikipedia.org/wiki/Merge_sort
[linear search]: https://en.wikipedia.org/wiki/Linear_search
[binary search]: https://en.wikipedia.org/wiki/Binary_search_algorithm
[linked list]: https://en.wikipedia.org/wiki/Linked_list
[hash table]: https://en.wikipedia.org/wiki/Hash_table
[array]: https://en.wikipedia.org/wiki/Array_data_structure
[tree]: https://en.wikipedia.org/wiki/Tree_(data_structure)
[binary search tree]: https://en.wikipedia.org/wiki/Binary_search_tree
[stack]: https://en.wikipedia.org/wiki/Stack_(abstract_data_type)
[queue]: https://en.wikipedia.org/wiki/Queue_(abstract_data_type)
[Wikipedia]: https://www.wikipedia.org/


### Phone call

The recruiter was very friendly during the call: we started by talking about completely unrelated topics, like the
weather and city life, before moving on to the actual skills evaluation. We touched on almost everything from the above
list and I also received a few questions about [dynamic programming] and [recursion]. A couple of times I struggled with
properly naming some terms and operations. Recruiters usually cannot dive deeply into technical topics, but she was very
open to discussing the reasons I used to name them differently.

Finally we discussed a few situational questions. I didn't have anything prepared, so had to remember and come up with
matching stories for each question right there.

She then expressed her positivity about my skills and we ended up the call. At the same moment I ordered an interview
preparation book (listed in the [References] section). And I ordered it on Amazon, by the way.

[dynamic programming]: https://en.wikipedia.org/wiki/Dynamic_programming
[recursion]: https://en.wikipedia.org/wiki/Recursion_(computer_science)
[References]: #references


June 2: On-site interview
-------------------------

Shortly the same recruiter contacted me with two emails: one had interview preparation tips and resources while the
other was an application form to fill in. The questions were mainly about my current status, how Amazon could help me
with relocation (if needed at all), current job conditions in terms of salary and perks, and the preferred day and time
for the on-site interview.

I filled it in and sent it back, and four days later I received a confirmation of the day and time of the on-site
interview. It was a new recruiter from the Berlin office. A week after she sent me a detailed schedule along with the
interviewers' names and titles. At that point it was helpful for me to look at their profiles on LinkedIn to get an idea
of whom I was going to talk to.


### Preparation

In total I had a little less than one month to prepare for the interview. I knew I wouldn't be able to finish the
interview preparation book completely, so I decided to solve three exercises from each section. The whole thought
process as well as iterations over solutions were translated onto paper and then compared to the answers at the end of
the book. *Black-color pen was used to write solutions, while red-color pen was used to mark errors. The idea was to
have less red with every following exercise*.

Another good source I found for practicing coding skills was [LeetCode]. As a coincidence, a friend of mine decided to
brush up on his skills too, so we dedicated two hours of each Thursday evening to work on LeetCode problems together.

Two weeks before the date I started writing stories for the behavioral questions. Most people tend to underestimate them
and focus mainly on the technical side. This is wrong! *Interviewers want to know you as a human being and understand if
they want to work with you on the same team*. What I found useful for myself was writing each story in a [STAR] format.
I worked on following situations: challenging problems, mistakes and failures, conflict handling, leadership examples.
As advice, try to *focus your stories on yourself and not on a team you cooperated with*. That way, it will be easier
for your interviewers to properly assess your contributions.

*You should know exactly why you want to work for Amazon*. If you don't, think twice about whether it's the right place
for you. Interviewers will know if you're not honest with them, and it will be a waste of time for all parties. After
all, why would you spend precious years of your life on something you're not truly passionate about?

*Make sure you can talk about yourself*. That includes both your story, which ideally covers your education, motivation,
and highlights in your professional career, and your strengths and weaknesses. You might also want to prepare all the
questions about the company or the teams you will be working with in advance.

[LeetCode]: https://leetcode.com/
[STAR]: https://en.wikipedia.org/wiki/Situation,_Task,_Action,_Result


### Interview day

Candidates were asked to come in 10 minutes earlier to register at the welcome desk. I had to bring a passport and sign
an NDA. One of the employees then welcomed me and took me to an interview room.

There were four 50-minute interviews in a row with a 10-minute break between them, and 15 more minutes before the last
one. Each interview contained 40 minutes of problem-solving and 10 minutes of behavioral questions.

For the first interview I had to solve an object-oriented design problem. I had to build an interface that client
developers would use to build libraries on top of. It starts off easy and as you progress, the interviewer adds more
requirements and problems to solve. It was followed by the behavioral question on how I dealt with a failed deadline.

The most important advice at this point - *do NOT start solving problems until you fully understand them. Think of
these interviews as brainstorming sessions - talk to your interviewer, ask him questions, discuss your solutions, and
when you know exactly what you are supposed to do, go ahead and do it*.

Another important advice - *if you're stuck, do ask for a help*. The worst thing you can do is quietly stare at the
whiteboard having no idea of what to do next.

For the second interview I was asked to solve a product-focused algorithmic problem. I needed to find the right
approach, identify appropriate data structures and algorithms, and write a code to get the problem solved. In the last
10 minutes we talked about the situation where I had a conflict with my teammate.

For the third interview I was building a system design for various product use cases. I was drawing system components on
the whiteboard, explaining how they communicate and what they are responsible for. As a situational question I was asked
if in my professional experience I had worked on something without getting approval from my manager.

The last interview was a purely technical, algorithmic problem. It was relatively easy, so I started by asking whether I
should provide the basic solution or start with an optimized one right away. He asked me to do the basic solution first
followed, of course, by its optimization. We iterated several times on that before we ran out of time. The interviewer
then asked me to tell a situation where I would have done something differently from what I actually did.

When you get out of the interview, you have a feeling that you failed completely, since you couldn't get any problem to
the point where interviewer would have said, "Great! Now that's the perfect solution!" Let me assure you - that is fine!
You are not supposed to find it. *Interview problems are designed exactly in this way, where you won't be able to
provide a complete solution in 40 minutes. Instead, interviewers want to see how far you can get and what your thought
process looks like*.


June 16: Offer
--------------

It took Amazon eight days to make a decision. A recruiter from the Berlin office sent me an email on Friday evening
saying that I was selected for the position. We discussed details on Monday, and three days after, on June 16th, I
received the final offer with the numbers.

Following day we clarified a list of questions I had as well as a few others I needed for my resignation process at my
current company. Shortly after an official YES was sent to Amazon.


References
----------

- [Which algorithms/data structures should I “recognize” and know by name?](http://programmers.stackexchange.com/a/155649)
- [Big-O Cheat Sheet](http://bigocheatsheet.com/)
- [Cracking the Coding Interview, 6th Edition](https://www.amazon.com/dp/0984782850)
- [Problems \| LeetCode OJ](https://leetcode.com/problemset/algorithms/)


Acknowledgements
----------------

[Anton Popov] mentored me throughout the hiring process and discussed drafts of this post together with [Sherzod
Abdujabborov] and [Umed Khudoiberdiev].

[Anton Popov]: https://de.linkedin.com/in/antonpopovprofile
[Sherzod Abdujabborov]: https://de.linkedin.com/in/sherzoda
[Umed Khudoiberdiev]: https://github.com/pleerock

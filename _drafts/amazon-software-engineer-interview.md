---
layout:      post
comments:    true
title:       Amazon software engineer interview
description: >
    Personal experience on being hired as a software development engineer at Amazon. Detailed interview process and
    preparation tips.
---

![Amazon - We Pioneer](/assets/amazon-we-pioneer.jpg)

I was recently contacted by a technical recruiter from Amazon. The company was hosting an interview event for software
engineers to join their team in their Berlin office.

The whole process from being contacted to signing the contract took two months. I would like to share my experience on
how it went in general as well as what I believe helped me to pass it successfully.

If I failed to mention something important in this article, feel free to start a discussion in the comments section.
There I will try to be as detailed as possible.

<!--more-->


April 27: First contact
-----------------------

I was contacted by the recruiter via [LinkedIn]. She told me they were looking for software engineers to join their team
in their Berlin office and asked me to send her an updated resume in case it sounded interesting for me. I always tend
to keep my resume updated, so the next day I sent her an email with it attached.

She responded with some general information about the role and the interview process. The first step was to conduct a
technical exercise via [Hackerrank], which I received a link for separately on the same day.

The exercise was limited to 120 minutes and the recruiter requested that I finish it before May 5th.

[LinkedIn]: https://www.linkedin.com/
[Hackerrank]: https://www.hackerrank.com/


May 1: Prescreening
-------------------

I decided not to rush and waited for the upcoming weekend.

Hackerrank has its own interview platform called [Hackerrank for Work]. That was the tool I landed on when I clicked on
the link in the email. It has a built-in timer, a web editor with some sort of autocompletion for Java, problem
statements and the ability to try your solution with various test cases including your own.

It was never communicated which languages the coding test would be limited to, which ruined my plans to use [Go] or
[PHP] - the languages I was the most proficient in. Those I could choose from were C, C++, Java and a couple of others,
so I ended up choosing [Java].

The test consisted of three problems which could technically be solved in no particular order.


### Problems

The first problem was related to an object-oriented design. I was provided with a few classes and their methods'
definitions to solve the problem in the most efficient way while maintaining clean, readable code.

The second problem was an algorithmic one. Here I will give you some advice which helped me personally: *do not focus on
thinking about which data structures and algorithms should be used for a particular problem, but rather on the problem
itself*. I tried to manually solve it on paper, realized how easy it was and then transferred my solution into the code.

However, a mistake I made was trying to further optimize the code and make it as beautiful as possible. I already had
all the test cases passing and should have instead used the remaining time to finish the last problem. Bad
prioritization. Lesson learned.

The third and the last problem was about analyzing complexity for the solution given in the previous problem. I was
expected to explain it as well as justify why I thought it was best from my point of view, but covered only the main
aspects due to the lack of time.

[Hackerrank for Work]: https://www.hackerrank.com/work
[Go]: https://golang.org/
[PHP]: http://php.net/
[Java]: https://www.oracle.com/java/index.html


May 4: Phone screening
----------------------

On the next day I received an email from the recruiter congratulating me on passing the technical exercises and asking
about my availability for the week to schedule a phone call where she was supposed to review my technical skills before
she could invite me to the on-site interview. We agreed on May 4th.


### Preparation

I only had two days so I brushed up on the essentials in algorithms and data structures. You can find such collections
everywhere. I've added the one that made the most sense for me to the [References] section.

Specifically, I focused on the following:

- Sorting: [bubble sort], [quicksort], [merge sort]
- Search: [linear search], [binary search]
- Data structures: [linked list], [hash table], [array], [tree], [binary search tree], [stack], [queue]

Of course, *you need to be able to argue about the complexity of algorithms and common operations on data structures*.
I personally found [Wikipedia] to be a great resource for this kind of analysis.


### Phone call

We had a call on the above date. The recruiter was very friendly: we started the call by talking about completely
unrelated topics, like the weather and city life, before moving on to the actual skills evaluation. We touched on almost
everything from the above list and I also received a few questions about [dynamic programming] and [recursion]. A couple
of times I struggled with naming some terms and operations properly. Recruiters usually cannot dive deeply into
technical topics, but she was very open to discussing the reasons I used to name them differently.

At the end of the call we discussed a few situational questions. I didn't have anything prepared, so had to remember and
come up with matching stories for each question right there.

She then expressed her positivity about me and we ended up the call. At the same moment I ordered an interview
preparation book (listed in the [References] section). And I ordered it via Amazon, by the way.

[References]: #references
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
[dynamic programming]: https://en.wikipedia.org/wiki/Dynamic_programming
[recursion]: https://en.wikipedia.org/wiki/Recursion_(computer_science)


June 2: On-site interview
-------------------------

On the next day after the phone screening the same recruiter contacted me with two emails: one had interview preparation
tips and resources while the other was an application for me to fill in. The questions were mainly about my current
status, how Amazon could help me with relocation (if needed at all), current job conditions in terms of salary and
perks, and the preferred day and time for the on-site interview.

I filled it in and sent it back, and in four days I received a confirmation of the day and time of the on-site
interview. It was a new recruiter from the Berlin office. In one more week she sent me a detailed schedule along with
the interviewers' names and titles. At that point it was helpful for me to look at their profiles on LinkedIn to get an
idea of whom I was going to talk to.


### Preparation

In total I had a little less than one month to prepare for the interview. I knew I wouldn't be able to finish the book
completely, so I decided to take three exercises from each section and solve them on paper. The whole thought process
as well as iterations over solutions were translated onto paper and then compared to the solutions at the end of the
book. *Black-color pen was used to solve problems, while red-color pen was used to mark errors. The idea was to have
less red with every following exercise.*

Another good source I found for practicing coding skills was [LeetCode]. As a coincidence, a friend of mine decided to
brush up on his skills too, so we dedicated two hours of each Thursday evening to work on LeetCode problems together.

Most people tend to underestimate the behavioral questions and focus mainly on the technical side. This is wrong!
*Interviewers want to know you as a human being and understand if you're the one they would like to work with in a
team*. Therefore two weeks before the date I started writing stories for the behavioral questions. What I found useful
for myself was writing each story in a [STAR] format. I worked on following situations: challenging problems, mistakes
and failures, conflict handling, leadership examples. As advice, try to *focus your stories on yourself and not on a
team you cooperated with*. That way, it will be easier for your interviewers to assess your contributions properly.

*You should know exactly why you want to work for Amazon*. If you don't know, think twice about whether it's the right
place for you. Interviewers will know if you're not honest with them and it will be a waste of time for all parties. And
after all, why would you spend precious years of your life on something you're not truly passionate about?

*Make sure you can talk about yourself*. That includes both your story, which ideally covers your education, motivation,
and highlights in your professional career, and your strengths and weaknesses. You might also want to prepare all the
questions about the company or the teams you will be working with in advance.

[LeetCode]: https://leetcode.com/
[STAR]: https://en.wikipedia.org/wiki/Situation,_Task,_Action,_Result


### Interview day

Candidates were asked to come in 10 minutes earlier to register at the welcome desk and have someone to escort them to
interviewing rooms. I had to bring a passport for the registration and sign an NDA. A staff person then welcomed me and
took me to an interview room.

There were four 50-minute interviews in a row with a 10-minute break between them, and 15 more minutes before the last
one. Each interview was composed of 40 minutes of problem-solving and 10 minutes of behavioral questions.

For the first interview I had to solve an object-oriented design problem. I had to build an interface that client
developers would use to build their libraries on top of. It starts off easy and as you go on, the interviewer adds more
requirements or problems to solve. It was followed by the behavioral question on how I dealt with a failed deadline.

For the second interview I was asked to solve a product problem where I needed to find the right approach, identify
appropriate data structures and algorithms, and write a code that would get the problem solved. The last 10 minutes we
spent talking about the situation where I had a conflict with my teammate.

For the third interview I was building a system design for various product use cases. I was drawing system components on
the whiteboard, explaining how they communicate and what they are responsible for. As a situational question I was asked
if in my professional experience I had worked on something without getting approval from my manager.

The last interview was a purely technical, algorithmic problem. It was relatively easy, so I started by asking whether I
should provide the basic solution or start with an optimized one right away. He asked me to do the basic solution first
followed, of course, by improving it. We iterated several times on that before we ran out of time. The interviewer then
asked me if I could tell him something about a situation where I would have done something differently from what I
actually did.

When you get out of the interview, you have a feeling that you failed completely, since you couldn't get any problem to
its end where interviewer would have said, "Great! Now that's the perfect solution!" Let me assure you - that is fine!
You are not supposed to find it. *Interview problems are designed exactly in this way, where you won't be able to
provide a complete solution in 40 minutes. Instead, interviewers want to see how far can you get and what your thought
process looks like*.


June 16: Offer
--------------

It took Amazon eight days to make a decision. A recruiter from the Berlin office sent me a quick email on Friday evening
saying that I was selected for the position. We scheduled a call on Monday, June 13th, to discuss the details. Three
more days then passed, and on June 16th I received the final offer with the numbers.

I prepared the list of questions I sent back via the same email thread and asked for another call. On the next day we
clarified them over the phone as well as a few others I needed for my resignation process at my current company. At the
end of the same day an official YES was sent to Amazon.


June XX: Contract
-----------------

...


References
----------

- [Which algorithms/data structures should I “recognize” and know by name?](http://programmers.stackexchange.com/a/155649)
- [Cracking the Coding Interview, 6th Edition](https://www.amazon.com/dp/0984782850)
- [Problems \| LeetCode OJ](https://leetcode.com/problemset/algorithms/)

---
title: "Tips to ace in CKA and CKAD exam"
date: 2021-01-08T14:00:13+05:30
tags: [
    "kubernetes",
    "certification",
    "cka",
    "ckad"
]
categories: [
    "kubernetes",
    "certification"
]
draft: false
---

_This blog was originally featured as a [guide](https://www.civo.com/learn/tips-to-ace-cka-and-ckad-exams) in civo cloud community._

| ![cka-ckad](https://github.com/milindchawre/civo-k8s/raw/master/blog/cka-ckad/images/cka-ckad.png) | 
|:--:| 
| *CKAD and CKA Certificate* |

I recently passed both CKA and CKAD exams, scoring 98% and 96% respectively. In this blog, I want to share my overall experience and tips to crack these exams.

#### What is CKA?
CKA is the [Certified Kubernetes Administrator](https://www.cncf.io/certification/cka/) certification, which focuses on administrative skills of managing, troubleshooting and operating a kubernetes cluster. The CKA exam certifies that users can design, build, configure, and expose native cloud applications for Kubernetes. 

#### What is CKAD?
CKAD is the [Certified Kubernetes Application Developer](https://www.cncf.io/certification/ckad/) certification which focuses on developer skills for kubernetes cluster. The CKAD exam aims to guarantee that certification holders have the knowledge, skills, and capability to design, configure, and expose cloud-native applications for Kubernetes and also perform the responsibilities of Kubernetes application developers.

These certification are valid for a duration of 3 years (36 months).

#### Should I choose CKA or CKAD?
You can attempt both the exams, but CKA is more suitable for administrators while CKAD is more inclined towards developers. It's up to you to decide and attempt the exam you think would benefit you more. Nothing is stopping you from trying both, of course!

#### Exam Curriculum (as of kubernetes v1.19):

Both the exams are delivered online and consist of 15-20 performance-based tasks with a 2hrs duration. The content is as follows:

---
>**_CKA (~ 17 questions)_**
~~~
25% - Cluster Architecture, Installation & Configuration

15% - Workloads & Scheduling

20% - Services & Networking

10% - Storage

30% - Troubleshooting
~~~
---

>**_CKAD (~ 19 questions)_**
~~~
13% – Core Concepts

18% – Configuration

10% – Multi-Container Pods

18% – Observability

20% – Pod Design

13% – Services & Networking

8% – State Persistence
~~~

---

To know more, check out the [official site](https://github.com/cncf/curriculum) for the exam curriculum and what the sections contain.

#### Exam Pre-requisite:
- [Register](https://www.cncf.io/) for the exam. Once you register, it is valid for 1 year. So you have one whole year to schedule the exam. Also included is one free retake in case you fail the exam on your first attempt.
- Linux administration basics
- Basics of the vi editor
- Chromium based browser. Make sure your browser passes the [compatibility check](https://www.examslocal.com/ScheduleExam/Home/CompatibilityCheck).

##### Exam Preparation:

There are [lot of resources](https://www.google.com/search?q=cka+ckad+exam+tips) available out there to prepare for the exam. I am listing those which I followed and found useful:
- Enroll in the kodekloud udemy course the exam you wish to prepare for. The course links are below. These courses cover all the concepts and have lots of practice labs to prepare you for the exam. Also they are very cheap at less than $5.
- After enrolling in the course, you also gets access to the kodekloud slack community, where you can ask any questions, and learn from others.
- Once you complete these courses, practice all the labs and mock tests multiple times. I would recommend going through them at least 3-4 times, until you get to the speed required in the exam (completing the tests within half the time allowed), and scoring 100%.
- Practice more questions, mentioned in the link below.

Following these steps should be more than sufficient to pass the exam with a very good score.

---
>**_Course Link_**

**CKA:** https://www.udemy.com/course/certified-kubernetes-administrator-with-practice-tests/

**CKAD:** https://www.udemy.com/course/certified-kubernetes-application-developer/

---
>**_Practice Questions_**

**CKA**

https://github.com/alijahnas/CKA-practice-exercises

https://levelup.gitconnected.com/kubernetes-cka-example-questions-practical-challenge-86318d85b4d

**CKAD**

https://github.com/dgkanatsios/CKAD-exercises

https://github.com/bbachi/CKAD-Practice-Questions

https://codeburst.io/kubernetes-ckad-weekly-challenges-overview-and-tips-7282b36a2681

---

By dedicating a few hours every day, it's possible to get fully prepared within 6 weeks. Remember **PRACTICE PRACTICE PRACTICE**.

#### Exam Tips:

- Make most out of imperative commands. The [kubectl cheatsheet](https://kubernetes.io/docs/reference/kubectl/cheatsheet/) is your saviour.
- At the beginning of exam, remember to [set auto-completions and kubectl alias](https://kubernetes.io/docs/reference/kubectl/cheatsheet/#kubectl-autocomplete), it will save a lot of time.
- Make use of bookmarks. [This is the list](https://gist.github.com/milindchawre/3558fabd7ee9ed72123d4be5b23f338c) that I used.
- Whenever you delete any kubernetes resources, make use of `--force` flag to delete them faster without wait.
- During the exam, make sure to switch to correct cluster context using the command given at the top of every question. Make sure to run it before attempting every question.
- If you are not familiar with any question or problem, just flag it and come back later. Aim to complete ones you can do quickly and return to questions with time you have left.
- Get familiar with official [kubernetes documentation](https://kubernetes.io/docs/home/), especially practice all the questions using your own [bookmarks](https://gist.github.com/milindchawre/3558fabd7ee9ed72123d4be5b23f338c). This will speed you up during exam, since you will know where to look for particular information.
- Spend time depending on the weightage of the question. There is no point in spending 15 mins on a question with 2% weight. Skip those and come back later.
- During the exam, sometimes you need to ssh to another node or change to root user. Beware of where you are shelled to all the time on the bash terminal.
- Time management is very crucial, refer the section below on how to manage time wisely.

#### Exam terminal:
You will be entering your examination commands on a terminal. Its always good to know how your exam terminal will looks like. Go through [this official document](https://docs.linuxfoundation.org/tc-docs/certification/lf-candidate-handbook/exam-user-interface).
| ![exam-terminal](https://github.com/milindchawre/civo-k8s/raw/master/blog/cka-ckad/images/exam-terminal.png) |
|:--:|
| *exam terminal snaphot, originally taken from the [Linux foundation site](https://docs.linuxfoundation.org/tc-docs/certification/lf-candidate-handbook/exam-user-interface)* |


#### Bookmarks
You can use [bookmarks](https://gist.github.com/milindchawre/3558fabd7ee9ed72123d4be5b23f338c) during the exam, rather than searching in the kubernetes docs. Trust me, it saves lot of crucial exam time.
| ![cka-ckad-bookmarks](https://github.com/milindchawre/civo-k8s/raw/master/blog/cka-ckad/images/cka-ckad-bookmarks.png) |
|:--:|
| *bookmarks* |

#### Choose a fast and optimal way to solve the question
There can be more than one way to accomplish a task in the exam. Use the one which is faster. For example, to create a pod, make use of `kubectl run` command rather than writing kubernetes YAML manually. You will get scored irrespective of the way you used to accomplish this task.

Note that there is no constraint to use a specific method to solve a problem: if you’re comfortable editing YAML in vim, go for it. Likewise, you can use `kubectl` generators, copy/paste from the [kubernetes docs](https://kubernetes.io/docs/home/), or even edit a resource manually using `kubectl edit`. Refer to the [kubectl cheatsheet](https://kubernetes.io/docs/reference/kubectl/cheatsheet/), it's very handy during the exam.

#### Time management
You have 2hrs to solve 15-20 questions, so roughly 6-7mins per question. So time management is very crucial. The order in which you solve the question is very important. This is the process I followed while attempting every question:

| ![cka-ckad-flowchart](https://github.com/milindchawre/civo-k8s/raw/master/blog/cka-ckad/images/cka-ckad-flowchart.png) |
|:--:|
| *Exam Flow* |

This boiled down to:
- Read the question carefully. Try to understand what exactly needs to be done to get the result they ask for. Don't make any assumptions: follow the facts mentioned in the question.
- If you decide to attempt the question, run the `kubectl` context command given at the top of the question before attempting it.
- If you think the question is very simple and can be done very quickly then just go for it, don't even look at the weightage of the question.
- If the question is too big to answer straight away, but a little tricky and time consuming to solve regardless of the weightage, then just flag the question and move on.
- While solving the question, if you get an error and get stuck (or it would take more time to fix it), then just leave that question, flag it and move on. Flagging the question is very important, so that you can easily find and attempt it later.
- Once you solve the question, just do a quick verification of your answer. Remember to verify it quickly, taking too much time for verifcation after attempting each question will slow you down. Remember that you should plan to have to save some time (at least 10-15 minutes) at the end of the exam to verify all the answers again in bulk.
- Try to solve as many questions as possible in first half of the exam.
- Once you have answered all the questions you could and reach the end, then attempt all the flagged questions.

If you don't follow the above method and do this instead:
- Sequentially solving the questions.
- Getting stucked on a question (spending more than 6-8mins).
- Solving tricky, complex questions with less weightage at the beginning instead of breezing through the easier ones, consuming a lot of time.

This will put you under pressure with less time and more un-answered questions in hand. This will impact your score and overall exam result.

Everything here is the mind game, try to keep your calm.

#### Links to refer before exam
[Candidate Handbook](https://docs.linuxfoundation.org/tc-docs/certification/lf-candidate-handbook)

[Curriculum Overview](https://github.com/cncf/curriculum)

[Exam Tips](https://docs.linuxfoundation.org/tc-docs/certification/tips-cka-and-ckad)

[FAQ](https://docs.linuxfoundation.org/tc-docs/certification/faq-cka-ckad-cks)

[Certification and Confidentiality Agreement](https://docs.linuxfoundation.org/tc-docs/certification/lf-cert-agreement/)


#### Exam Day
- Try to schedule your exam for the morning, when your mind is fresh and free of other work related stress.
- Keep your room and desk clean.
- The exam duration is two hours, so carry a water bottle with you but note that it should be clear without any label. See below for how you will be monitored during the exam.
- Make sure to join at least 15mins prior to the exam start time.
- Your exam is monitored online by a proctor, who is very strict about exam code of conduct.
- Exam begins with verification of identity and compliance with the rules. You need to activate your camera and share your screen. This process would take somewhere around 30mins.
- Don't cover your mouth, read out questions aloud, move away from your desk or center of your camera - it's not allowed.
- All other instructions will be provided by the proctor before the exam. Strictly follow all those instructions.

#### Conclusion:
CKA and CKAD exams requires lot of hands on practice and skills. However, it is also one of the most rewarding experience. Even if you don't pass in first attempt, there is one free retake opportunity. Remember: **PRACTICE PRACTICE PRACTICE**.

I hope this helps you. Good luck and feel free to ask any questions. Connect me on [Linkedin](https://www.linkedin.com/in/milind-chawre) and [Twitter](https://twitter.com/milindchawre).


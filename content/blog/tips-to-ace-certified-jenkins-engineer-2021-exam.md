---
title: "Tips to ace Certified Jenkins Engineer 2021 exam"
date: 2021-06-16T11:49:26+05:30
tags: [
    "jenkins",
    "certification",
    "cje",
    "ccje",
    "ci-cd"
]
categories: [
    "jenkins",
    "certification"
]
draft: false
---

_This blog was originally featured as a [guide](https://www.civo.com/learn/tips-to-ace-certified-jenkins-engineer-2021-exam) in civo cloud community._

I recently passed the Certified Jenkins Engineer 2021 exam, scoring ~76%. This post talks about my overall exam experience and some tips.

| ![cje-cert](https://github.com/milindchawre/civo-k8s/raw/master/blog/cje/images/cje-cert.png) |
|:--:|
| *CJE Certificate* |

***Note:** This post is not about exam dumps, as it defeats the whole purpose of this exam which is for you to demonstrate your knowledge. Also due to the NDA I agreed to by signing up for the exam, I can't reveal any questions asked in this exam. Though I can provide some pointers to help you with the exam preparation and to give you overall idea about the nature of this exam.*

### Jenkins Certification
[Jenkins Certification](https://www.cloudbees.com/jenkins/certification) is a professional-grade certification that demostrates your understanding of CI/CD concepts and DevOps best practices as well as the major features of Jenkins and, optionally, CloudBees Core.

Attaining certifies status means you possess the skills and hands-on experience necessary to implement and use [Jenkins](https://www.jenkins.io/), a leading continuous delivery automation server.

There are two certifications available:
- **Certified Jenkins Engineer (CJE):** This tests your proficiency with Jenkins and CloudBees Jenkins Distribution (CJD).
- **Certified CloudBees Jenkins Engineer (CCJE):** This tests your knowledge about enterprise version of Jenkins - [Cloudbees Core](https://www.cloudbees.com/).

### CJE or CCJE?
The Certified Jenkins Engineer exam is more suitable if you mainly work with the open source version of Jenkins. If you use the cloud and enterprise version of Jenkins then go with the CCJE exam.

### Registering for the exam
The exam can be taken onsite at the [test centers](https://www.kryteriononline.com/Locate-Test-Center) or online from your home due to ongoing Covid situation. In case you opt for onsite test make sure that the [test center is available in your locality](https://www.kryteriononline.com/Locate-Test-Center).

Once you decide, go and [register for the exam](https://www.webassessor.com/wa.do?page=enterCatalog&branding=CLOUDBEES&tabs=111).

| ![jenkins-exam-registration](https://github.com/milindchawre/civo-k8s/raw/master/blog/cje/images/jenkins-exam-registration.png) |
|:--:|
| *Jenkins exam registration* |

While there is a cost to the exam, it is possible to get a free exam voucher from CloudBees by attending the [DevOps World event](https://www.cloudbees.com/devops-world).

### Exam curriculum
To get overall idea, make sure to go through the [exam guide](https://standard.cbu.cloudbees.com/certification-guide-and-information). The structure and topics are outlined below:

#### - Multiple-choice questions
The exam covers the current version of Jenkins, CloudBees Jenkins Distribution (and CloudBees Core only for CCJE exam) and have multiple-choice questions to solve.

**CJE:** 60 multiple-choice question about Jenkins and CloudBees Jenkins Distribution features in 90 minutes

**CCJE:** 90 multiple-choice questions (60 questions about Jenkins and CloudBees Jenkins Distribution features and 30 additional questions about CloudBees Core features) in 120 minutes

#### - Exam topics
The exam mainly covers topics related to Jenkins Fundamentals, Jenkins Administration, Jenkins Build Technologies: Pipeline, Jenkins Build Technologies: Freestyle and  CloudBees Core Features (CCJE exam only).
| ![jenkins-curriculum](https://github.com/milindchawre/civo-k8s/raw/master/blog/cje/images/jenkins-curriculum.png) |
|:--:|
| *Jenkins exam curriculum* |

#### - Exam scoring
To pass the exam you need to correctly answer at least 66% of the questions. Each question can have a single or multiple correct answers. Each correct answer worth a single point. The questions asked in the exam clearly mention if there are multiple or single responses to the question: you need to choose the correct radio button or tick the correct checkbox for a single-answer question, or the requisite number of checkboxes specified in the question.

For more information, read the [official certification guide](https://standard.cbu.cloudbees.com/certification-guide-and-information).

### Exam Preparation:
This is what I referred to in preparation for my exam:
- Cloudbees university course: https://standard.cbu.cloudbees.com/series/exam-preparation-certified-jenkins-engineer-cje
- Blogs: 
  * https://devopslearning.medium.com/my-road-to-certified-jenkins-engineer-807ae52409a0 
  * https://medium.com/@deepakr6242/top-ten-points-to-clear-certified-jenkins-engineer-in-a-month-for-free-a92d6d020a6e

The [cloudbees university CJE course](https://standard.cbu.cloudbees.com/series/exam-preparation-certified-jenkins-engineer-cje) covers almost every topic asked in the exam. It has many pointers with appropriate references to respective Jenkins documentation. The course also s hands-on labs to get acquainted with Jenkins.

To follow the course: go through each concept, work through associated practice labs and thoroughly read through the relevant Jenkins documentation.

The labs mentioned in the exam need Jenkins set up to work with. I found it difficult to setup the required Vagrant + Virtualbox on my windows workstation, so I quickly [set up jenkins on my civo kubernetes cluster](https://www.civo.com/learn/deploy-jenkins-from-the-civo-app-marketplace). I find it quite convenient to pratice Jenkins labs on my Civo cluster. If you haven't signed up for civo, [do it now](https://www.civo.com/signup).


### Is theory enough or do I need hands-on?
Many of us assume that multiple-choice question based exams can be cracked by just going through the theory, but in case of Jenkins you need to have some practical knowledge to ace this exam.

Basically the exam questions are of three kinds:
1. Straight forward question (you know the answer or not)
2. Question which need memorization (better to get some hands-on experience to know what the issue is, rather than memorizing)
3. In-depth question (you need more in-depth knowledge of a specific concept to answer it)

Some hands-on practice helps in solving the 2nd and 3rd kind of questions.

### Exam Terminal
This is how your exam terminal looks like.
| ![jenkins-terminal](https://github.com/milindchawre/civo-k8s/raw/master/blog/cje/images/jenkins-terminal.png) |
|:--:|
| *Jenkins exam terminal* |

- ***Time Remaining:*** Shows how much time left to finish the exam.
- ***Question:*** Describes the question in detail.
- ***Review Question Checkbox:*** You can mark the question to review it later. If I'm doubtful about my answer, I opt to review it later.
- ***Answer / Options to Choose:*** This section contains multiple radio button or checkbox options which you need to choose, to answer the question correctly.
- ***Test Aid:*** This section shows things that you can refer during the exam. For CJE exam none of these options are available.
- ***Back:*** To move to the previous question.
- ***Next:*** To move to the next question.
- ***Review All:*** Select this to review all the questions, usually done once you are finish answering all the questions and want to review any you may have doubts about.
- ***Submit Exam:*** Select this to finish the exam.

# Exam flow
You have 90 minutes to solve 60 questions in the CJE exam and 120 minutes to solve 90 questions in the CCJE exam. This works out to roughly 1.5 mins per question, so time management is very crucial.

This is the process I followed while attempting each question:
| ![jenkins-exam-flow](https://github.com/milindchawre/civo-k8s/raw/master/blog/cje/images/jenkins-exam-flow.png) |
|:--:|
| *Jenkins exam flow* |

You may have seen a similar flow if you have seen my [post on acing the CKA and CKAD exams](https://milindchawre.github.io/site/blog/tips-to-ace-in-cka-and-ckad-exam/).

### Exam Day
This all is advice that assumes the exam is online proctored.

Before the exam day:
- Refer to the [kryterion guide](https://kryterion.force.com/support/s/topic/0TO1W000000I5h3WAC/online-proctoring?language=en_US) before attempting the exam.
- Go through the [exam FAQ page](https://support.cloudbees.com/hc/en-us/articles/360046012631-CloudBees-Training-and-Certification-FAQ)
- Make sure your machine passes the [system check](http://www.kryteriononline.com/systemcheck).

On exam day:
- Make sure to appear at least 15 mins before the exam.
- Keep your personal documents handy, you might need it for ID verification. Though in my case, the system didn't ask for any ID, but its good to keep it handy.
- Make sure your room is quiet and your desk is clear.
- In online proctored exam, the exam launch button appears 10 minutes before the scheduled exam time. Make sure you are ready prior to that.

### After the exam
As soon as you finish the exam, the result is shown on your screen. It shows the overall percentage you got and your score in each section. If you fail the exam, the result helps in understanding which section you should focus on more for next time. Remember there is no free second attempt, you need to register and pay for the exam again.

| ![cje-score](https://github.com/milindchawre/civo-k8s/raw/master/blog/cje/images/cje-score.png) |
|:--:|
| *CJE exam score* |

### Conclusion
Both the CJE and CCJE exams require some basic knowledge about CI/CD concepts and some hands-on practice with Jenkins. I recommend you practice the hands-on labs to make sure you are familiar with the system. However, taking these exams is also one of the most rewarding experiences.

I hope this guide helps you in preparing for the exam. Good luck and feel free to ask any questions. You can connect with me on the [Civo community Slack](https://civo.io/slack), [Linkedin](https://www.linkedin.com/in/milind-chawre) and [Twitter](https://twitter.com/milindchawre).

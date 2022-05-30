---
title: "Getting started with machine learning"
date: 2022-05-03T20:41:03+01:00
draft: true
summary: "Have you wanted to understand machine learning, but didn't know where to begin? Whether you're a software developer wanting to broaden your skill set, or just curious about machine learning, this post is for you."
cover: 
    image: /getting-started-with-ml/ml-synapse.jpg
    alt: "diagrams showing common machine learning uses"

categories: ["ai"]
tags: ["machine learning"]
series: []

params:
    ShowShareButtons: true
    ShowReadingTime: true

---

## Why learn about ML?

There's a quiet revolution that's been underway for sometime. It's the revolution of how computers can be used to solve problems. 
Machine learning began in the labs many years ago and is now fully embedded in our lives. We'll look at some examples later in this post. 

Whether you're in a technology profession, or a consumer of technology, machine learning will increasingly dominate our lives, and so we can choose to either swim with the tide, or get carried away. We don't necessarily need to become experts, but we owe it to future selves to learn enough to be able to ask better questions. If you're a software developer, then understanding more about machine learning will expand your career options and help you navigate future 'build vs buy' decisions.  Don't let complacency lead to your obsolescence!

## Defining machine learning

Machine learning is a type of Artificial Intelligence (AI), with AI defined as non-biological intelligence, and intelligence defined as the ability to solve complex tasks. Machine learning leverages a combination of statistical and algorithmic techniques trained from example data in order to make predictions based on new data and improve its learning.

## What problems does it solve?

The traditional approach to solving problems using programmatic methods normally involves a series of instructions that execute step-by-step in a defined sequence.  A collection of rules are defined and evaluated based on inputs. This approach is fine for the vast majority of problems, but when the rules become complex or unmanageable, that's when example-based approaches are better. Machine learning is not necessarily a new way to solve familiar problems, but instead a way to solve new kinds of problems​.

For example, imagine if you were asked to write some code to determine whether a picture contains a fish. Where would you start? Well, you might begin by defining a shape of a fish to look for in a picture, but there are many different shaped fish, the angle of the fish in the image may vary along with the colour of the fish against the background. How could you build rules for every possibility? The answer: use a machine learning example-driven approach. Train a machine learning model to recognise a fish from a large set of examples that contain variety of breeds, shapes, sizes, angles, lighting and colours.  

In practice, machine learning is really good at solving certain problems:

![examples of machine learning](/getting-started-with-ml/ml-uses.jpg)

- Classification (what type of thing is this?)
- Regression (what is the predicted value?)
- Clustering (what related data can be grouped together?)
- Anomaly detection (what data is out of place?)

## How do you teach a machine?

Machine learning can be divided into supervised learning, where information models are trained with labelled examples, and unsupervised learning, where the machine learning process is left to discover patterns, or relationships in the data. 

Supervised learning focuses on supporting the learning processing through many examples of data that are labelled, that is, examples that contain a description of the input data is. The greater the number of examples used in the training process, the better, although there's a trade between the accuracy of the output, and time to train the model. 

Let's look at some examples of supervised and unsupervised learning.

## Everyday machine learning 

Machine learning impacts our day-to-day lives in more ways than we realise, for example:

#### Unsupervised learning 
- Online banking: is this transaction fraudulent?
- Customer analysis: what personas or groups exist in our customer base?​

#### Supervised learning 
- Money lending and insurance: is this customer a safe bet?
- Customer analysis: is this customer likely to leave our service?
- Facial recognition: unlocking your with your face phone, face mapping onto emojis
- Content moderation: does an image or written text contain offensive material?
- Sentiment analysis: are our customers speaking positively or negatively about us on social media?
- Medical diagnosis: does a scan from an x-ray, MRI, or CT scan contain signs of disease?
- Self-driving cars: what action should the car perform based on sensors input?
- Visual search: does this picture match the supplied text description?
- Image description: generate a textual description to represent the contents and intent of an image 
- 

## Machine learning in action ##

It's helpful to see machine learning in action. Daniel Shiffman, better known as the author of [The Nature of Code](https://natureofcode.com/) and presenter of [The Coding Train](https://thecodingtrain.com/), has an excellent entry-level video where [he demonstrates how Google Teachable Machine](https://www.youtube.com/watch?v=kwcillcWOg0&list=PLRqwX-V7Uu6aJwX0rFP-7ccA6ivsPDsK5) can recognise a few objects. Take a look at his video and then try it yourself at [Google Teachable Machine](https://teachablemachine.withgoogle.com/)


![teachable machine](/getting-started-with-ml/teachablemachine.jpg)

So what's happening within Google Teachable Machine? This is supervised learning and classification in action. In this case, recognising a number of images through examples, and associating the set of training images with a name, or label. Once trained, the model is tested with new images from a webcam, and a percentage confidence score is displayed indicating the accuracy of the classification.
 

## Thinking different ## 

Because machine learning is based on statistical analysis, the outputs of a model are probabilities, that is the likelihood, or confidence. And because of this, we need to shift our thinking away from exact answers towards statistical probabilities. Coupled with this, randomness is often used when training the model to improve efficiency, so if we're to retrain a model from scratch with the same training data, we may not achieve exactly the same results. This is a very different world from rule-based problem solving where the outcomes are deterministic and distinct. 


## What are the limitations? ##

As with any technology, there are limitations and constraints. There are three areas that cause concern with many observers.

- Bias  
- Transparency 
- Ethics 

**Bias** can be present in supervised machine learning models because of inherent human bias when choosing the training set. For example, facial recognition systems can be poor at recognising a diverse set of faces if there's limited ethnic diversity in the training image set. This may not be intentional, but instead a clumsy or lazy approach towards ensuring a robust model. In [Hello World](), Hannah Fry has some excellent examples of algorithmic bias from law to XXXX 

**Transparency** addresses the question of how a explainable a system is. Can we we clearly describe the conditions, steps and reasoning that led to a particular output? Why is this important? Imagine there's a system that's in charge of making a life-changing decision, say a money lending system, that determines your suitability for a loan, or an interview system that determines your suitability for a role? We would want to know how the system arrived at a particular decision and that the process was fair and explainable.

**Ehtics** represents the collective societal values of individuals, whereas **morals** represent what we consider as individuals to be fair, right and just. The problem is that in the the race to invent and innovate with new and little understood technology, ethical considerations can be an afterthought. Designers of machine learning systems need to be aligned with our values. Take for instance, self-driving cars. We want self-driving cars to be safe and to protect the car's occupants as well as pedestrians and other vehicle drivers. Although we're not yet at the stage of fully autonomous vehicles [despite the hype](https://medium.com/predict/elon-musks-autopilot-hype-has-now-risen-to-gross-negligence-612d262e3220), the AI inside these systems will be faced with moral dilemmas in the event of catastrophic mechanical failure where either the occupant or those around the vehicle face peril. This very scenario is explored in the [Moral Machine](https://www.moralmachine.net/) where you get to play the part of decision-making process in various fictitious scenarios. As part of the test, your're asked to decide between saving groups of individuals where loss of life is certain. While some of the scenarios feel a little extreme, and it has to be said, a little dark, it's interesting to explore our own morals and compare them with other people's.

## Where to next?

For developers 

- The [Coding Train playlist on ml5.js]() is great way to experiment with machine learning in a web browser without having to set up complex development environments

- Jason Brownlee, the mind behind [Machine Learning Mastery](https://machinelaarningmastery.com), has an excellent series of learning paths and books to accelerate your learning and take you from beginner to expert 

## For curious minds ## 

- [Future of life Institute](https://www.futureoflife.org) is a non-profile organisation exploring the global existential risks of powerful technologies. They are focused on AI, biotech, weapons and climate. There are lots of thought-provoking discussions on there from leaders in tech industries, along with a number of ways to get involved in the conversation. 


- [Open AI](https://openai.org) is a non-profit AI R&D company whose mission is to ensure that artificial general intelligence benefits all of humanity. They have a guiding charter and they are using their expertise and influence to guide AI in the right direction. You'll find many ground-breaking projects and advances here, many of which you can experiment with. Interestingly, they've formed an alliance with Microsoft and as such, we'll start to see many of the open source projects appearing as hosted services in the Azure cloud.
 

- [Life 3.0]() is fascinating book by physicist, Max Tegmark, in which he explores the future of humanity and intelligent machines. A number of different scenarios are considered, both good and bad, but he's ultimately optimistic that AI can be beneficial for humanity. That is as long as we start tackling the hard problem of keeping our AI overlords aligned with our values. It's a great read, or listen if you're into audiobooks.


I hope this post has given you a few paths to explore machine learning and expand your knowledge. It's a fast-changing area, but it's still possible to keep an eye on developments without becoming an expert. In following posts, I'll walk through some interactive machine learning examples and we'll understand how to build simple examples with the [ml5.js](https://learn.ml5js.org/) JavaScript library.



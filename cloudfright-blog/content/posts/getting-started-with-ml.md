---
title: "Getting started with machine learning"
date: 2022-05-03T20:41:03+01:00
draft: true
summary: "Have you wanted to understand a little more about machine learning, but didn't know where to begin? Whether you're a software developer wanting to broaden your skill set, or just curious about machine learning, this post is for you."
cover: 
    image: 
    alt: ""

categories: ["ai"]
tags: ["machine learning"]
series: []

params:
    ShowShareButtons: true
    ShowReadingTime: true

---

## What's in it for you? ##

There's a quiet revolution that's been underway for sometime. It's the revolution of how computers can be used to solve problems. 
Machine learning began in the labs many years ago, has grown in popularity and fully embedded in our lives. We'll look at some examples later in the post. 

Whether you're in a technology profession, or a consumer of technology, machine learning will increasingly dominate our lives, and so we can choose to either swim with the tide, or get carried away. We don't necessarily need to become experts, but we owe it to ourselves and our careers to learn enough to be able to ask better questions. If you're a software developer, then understanding more about machine learning will expand your career options and help you navigate future 'build vs buy' decisions.  Don't let complacency lead to your obsolescence!

## Defining machine learning ##

Machine learning is a type of Artificial Intelligence (AI), with AI defined as non-biological intelligence, and intelligence defined as the ability to solve complex tasks. Machine learning leverages a combination of statistical and algorithmic techniques fed from example data in order to make a prediction based on new data and improve its learning.

## What problems does it solve? ##

The traditional approach to solving problems using programmatic methods normally involves a series of instructions that execute step-by-step in a defined sequence.  A collection of rules are defined and evaluated based on inputs. This approach is fine for the vast majority of problems, but when the rules become complex or unmanageable, that's when example-based approaches are better. Machine learning is not necessarily a new way to solve familiar problems, but instead a way to solve new kinds of problems​.

For example, imagine if you were asked to write some code to determine whether a picture contains a fish. Where would you start? Well, you might begin by defining a shape of a fish to look for in a picture, but there are many different shaped fish, the angle of the fish in the image may vary along with the colour of the fish against the background. How could you build rules for every possibility? The answer: use a machine learning example-driven approach. Train a machine learning model to recognise a fish from a large set of examples that contain variety of breeds, shapes, sizes, angles, lighting and colours.  

In practice, machine learning is at solving certain problems:

- Classification (what type of thing is this?)
- Regression (what is the predicted value?)
- Clustering (what related data can be grouped together?)
- Anomaly detection (what data is out of place?)

## How do you teach a machine ? ##

Machine learning can be divided into supervised learning, where information models are trained with labelled examples, and unsupervised learning, where the machine learning process is left to discover patterns or relationships in the data. 

Supervised learning focuses on supporting the learning processing through many examples of data that are labelled, that is, examples that contain a description of the input data is. The greater the number of examples used in the training process, the better, although there's a trade between the accuracy of the output, and time to train the model. 

Let's look at some examples of supervised and unsupervised learning.

## Everyday machine learning  ## 

Machine learning impacts our day-to-day lives in more ways than we realise, for example:

## Unsupervised learning 
- Online banking: is this transaction fraudulent?
- Customer analysis: what personas or groups exist in our customers?​

## Supervised learning 
- Money lending and insurance: is this customer a safe bet?
- Customer analysis: is this customer likely to leave our service?
- Facial recognition: unlocking your with your face phone, face mapping onto emojis
- Content moderation: does an image or written text contain offensive material?
- Sentiment analysis: are our customers speaking positively or negatively about us on social media?
- Medical diagnosis: does a scan from an x-ray, MRI, or CT scan contain signs of disease?
- Self-driving cars: what action should I perform next based on what my sensors are telling me?
- Visual search: does this picture match the supplied text description?
- Image description: generate a textual description to represent the contents and intent of an image 
- 

## ML in action ##

It's helpful to see machine learning in action. Daniel Shiffman, better known as author of [The Nature of Code]() and presenter of [The Coding Train]() has an excellent entry-level video where he demonstrates how Google Teachable Machine to recognise a few objects. Take a look at this and then try it yourself at [Google Teachable Machine]()

Embed video

Screenshot of teachable machine 

 So what's happening within Google Teachable Machine? This is supervised learning and classification in action. In this case, recognising a number of images through examples, describing the set of training images with a name. Once trained, the model is tested with new images from a webcam and a percentage confidence score is displayed indicating the accuracy of the classification.
 

## Thinking different ## 

Because machine learning is based on statistical analysis, the outputs of a model are probabilities, that is the likelihood, or confidence. And because of this, we need to shift our thinking away from exact answers towards statistical probabilities. Coupled with this, randomness is often used when training the model to improve efficiency, so if we're to retrain a model from scratch with the same training data, we may not achieve exactly the same results. This is a very different world from rule-based problem solving.


## What are the limitations? ##

As with any technology, there are limitations and constraints. There are three areas that cause concern with many observers.

- Bias  
- Transparency 
- Ethics 

Bias can be present in supervised machine learning models because of inherent human bias when choosing the training set. For example, facial recognition systems can be poor at recognising a diverse set of faces if there's limited ethnic diversity in the training image set. This may not be intentional, but instead a clumsy or lazy approach towards ensuring a robust model. In [Hello World](), Hannah Fry has some excellent examples of algorithmic bias from law to XXXX 

Transparency addresses the question of how a explainable a system is. Can we we clearly describe the conditions, steps and reasoning that led to a particular output? Why is this important? Imagine there's a system that's in charge of making a life-changing decision, say a money lending system, that determines your suitability for a loan, or an interview system that determines your suitability for a role? We would want to know how the system arrived at a particular decision.

Ehtics represents the collective societal values of individuals, with morals representing what we consider as individuals to be fair, right and just. The race to invent and innovate with new and little understood technology can be at odds with ethics because individuals mat 


We want designers of machine learning systems to be aligned with our values. Take for instance, self-driving cars. We want those cars to be safe and to protect the car's occupants as well as pedestrians and other vehicle drivers. Although we're not yet at the stage of fully autonomous vehicles [despite the hype](), the AI inside these systems will be faced with moral dilemmas in the event of catastrophic mechanical failure where either the occupant or those around the vehicle face peril. This very scenario is explored in the [Moral Machine]() where you get to play the part of decision-making process in various fictitious scenarios. As part of the test, your're asked to decide between saving groups of individuals where loss of life is certain. While some of the scenarios feel a little extreme, it's interesting to explore our own morals and compare them with other people's.

## Your next steps ##

For developers 

- The [Coding Train playlist on ml5.js]() is great way to experiment with machine learning in the browser without needed to set up complex development environments

- Jason Brownlee, the person behind [Machine Learning Mastery](https://machinelaarningmastery.com) has an excellent learning path and book selection to accelerate your learning to take you from beginner to expert 

## For curious minds ## 

What examples can you uncover in your everyday life that use machine learning? AI and ML is set to get more powerful and pervasive​ and so we need arm ourselves with the knowledge to understand what it means for us.​

- [Future of life Institute](https://www.futureoflife.org) is a non-profit organisation   


- [Open AI](https://openai.org) is 

- [Life 3.0]() in this book, Max Tegmark explores what life might be like in the future as the search for human level general intelligence in machines leads to super intelligence - intelligence way beyond human intelligence. He looks at possible futures both good and bad, but is hopeful that humanity can give birth to beneficial AI as long we can address the hard problems safety and control, along with aligning humanity's goals with that of any super intelligent machines.






Architectures 
Neural networks and interconnected computational nodes, are used to create structures that influenced by the connectivity of the brain. This approach is called deep learning. 
# dcgan-criminal-sketches

Human forensics artists/criminal sketch artists' abilities are limited by many factors; lack of experience, artistic ability, fatigue, or even physical number of human artists available can result in subpar criminal sketches. 

A lack of professional forensic artists in an area can result in witnesses and victims having to wait weeks before being able to get a criminal sketch. This is not only unfair, but also highly inefficient, as human memory fades significantly with time. It also comes at no surprise that less affluent areas have reduced access to or quality of criminal sketching services, due to any of the limitations mentioned above.  

This is an often-ignored problem, but it is very serious for those who are unfortunate enough to fall victim to criminal activity. By the philosophy of our criminal justice system, each person should have an equal right to criminal justice. The flaws in the forensic sketch department, however, systemically deprives inhabitants of certain areas of an important and rightful part of criminal justice. 

## Objective:

AI using GAN to generate criminal sketches, given witness descriptions. 

## Problem Statement:

"The point of the sketch is not to make a portrait or an identical match of the perpetrator. The point is to get to a resemblance, so that people can look at the drawing and be reminded of someone that they have seen recently or in the past" (Victor). 

While the AI is similar to human forensic artists in the fact that photos generated may not be a perfect replica of the perpetrator's face, the AI has many other advantages. For one, it can generate multiple human faces in a significantly shorter span of time than the hours that it may take for a human artist. AI also has a higher capacity for "experiential learning." While human artists must work with the problem of limited memory over time, AI actually grows more accurate the more data (photos) it is fed. 

The process of human artists creating sketches often involving looking through thousands of real human photographs just to generate a single sketch:
"We moved on to the FBI picture book, where there were hundreds, maybe thousands, of pictures of people (noncriminals) separated into different features—from face features to type of hats to hair. She needed more detail to complete the sketch, so she took me through the different sections and asked me to take a look at the pictures and identify the closest picture to the feature...His cheekbones were a combination of two pictures, and so forth. She made notes of each picture I cited for each feature…" (Victor).

However, human artists require a much longer time to scan through so many photographs, and even so, cannot really "merge" multiple features into a photograph (they sketch it by hand). AI, on the other hand, can actually synthesize multiple features into a realistic-looking photograph. 

Usage of AI to create criminal sketches can drastically benefit underprivileged communities. Not only would we be helping every victim take full advantage of their rights, we would be improving the quality of these "sketches," as witnesses would be able to list perpetrators' characteristics before they fade from memory over weeks. AI would be able to save precious time and better maintain the equal right to justice for all Americans, regardless of where they live. 

## Potential Problems/Flaws:
The main problem of this idea is very similar to the problem of AI-generated recidivism scores:
- Systemic over or under-representation of certain peoples in the data can lead to bias in the generated photos
- Pavlovian effect and/or Placebo effect: if criminal sketches generated repeatedly contain features of any overrepresented group, civilians who see criminal sketches may be subconsciously conditioned to associate that overrepresented group with criminal activity
- May lead to negative stereotyping 
- Potential privacy concerns in data sets

## Algorithm(s): GAN (Generative Adversarial Network) + (potential) using IBM-Q cloud quantum computer

## Overview of the project and the reasons to use GAN:
Through this project, we wanted to explore architectures that could help us achieve our tasks of generating images from given text descriptions.
One of the most challenging problems of the world of computer vision is synthesizing high-quality images from text descriptions. No doubt, this is interesting and useful, but current AI systems are far from this goal. Although with the advent of powerful neural networks architectures like GAN’s, it is now possible to generate good results.

Link for labelled dataset of faces: http://mmlab.ie.cuhk.edu.hk/projects/CelebA.html

## Two-step Implementation Plan:

### 1st layer (bulk work done here): implementing the code to generate realistic random human faces
This is the link for a dataset that includes only cropped faces: 
http://mmlab.ie.cuhk.edu.hk/projects/CelebA.html
https://drive.google.com/drive/folders/0B7EVK8r0v71pOC0wOVZlQnFfaGs


### GAN Implementation:
• Generator and Discriminator neural network pair - adversarial and zero-sum pair
• Generator tries to generate data (photo) indistinguishable from the real data that it is fed
• Discriminator tries to distinguish if the data (photo) passed to it is "real" or generated by the Generator
• Train these networks against each other in mini-max game where the two take optimal steps to "fool" each other
• Key points to refer to while training a GAN:
 - Discriminator = Minimizer
 - When training Discriminator, hold Generator values constant
 - Generator = Maximizer
 - When training Generator, hold Discriminator values constant
 - The two neural networks must have a similar skill level
 - Want to eventually get to point where Discriminator can't tell difference b/w "real" & generated data (photo)
• Ultimate goal: Maximizer (Generator) "wins"
GitHub link  for a DCGAN image generator (reference) : https://github.com/gsurma/image_generator


### 2nd layer: add a natural language processing layer, to synthesize and transcribe witnesses' descriptions into a single picture 
- Data specifically labelled/classified as specific characteristics (sufficiently large data set absolutely necessary for this step)
Ex: "blue eyes," "beard," "black hair," "eyebags"

## References: 
1) https://arxiv.org/abs/1812.04948
2) http://arxiv.org/abs/1912.04958

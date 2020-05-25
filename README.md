# Generating Characters from Cartoon Images

DSC160 Data Science and the Arts - Final Project - Generative Arts - Spring 2020

Project Team Members: 
Yuxi Luo, yul884@ucsd.edu
Emily Kwan, ekwan@ucsd.edu
Ittoop Shinu Shibu, ishibu@ucsd.edu
Pratyush Juneja, pjuneja@ucsd.edu
Eric Yu, ery010@ucsd.edu 

## Abstract

Our concept for a generative art project is implementing a deep learning approach to create new instances of characters from media using existing samples. Specifically, we can take data-sets consisting of images of characters from well-known games, cartoons, or movies and use neural networks to output images of newly-created characters not from the original data-set. Typically, this method is done using generative adversarial networks (GANs), which consists of two “competing” networks, a generator and a discriminator. We plan to implement StyleGAN (a modified architecture of GANs), to experiment with the data. We will also need techniques for scraping, cleaning, and exploring our data-sets. With multi-channel image data, we may also need to perform some preprocessing to ensure that our pipeline’s computational requirements are reasonable. Neural networks are known to be computationally expensive when used with large image data-sets, so we may have to modify our data (resize, threshold, etc.) to make it work in a reasonable amount of time/GPU resources. An example of this type of project has been done previously with a Pokemon image data-set: How To Create Unique Pokémon Using GANs. 

For training data, we plan to use images of characters from games or cartoons (for example, the Pokemon data-set). The hope is that the network we choose is robust (and efficient) enough to generate instances of characters that remotely resemble any of the examples from the training set. Ideally, we would like to see some images of characters that possess qualities from different samples from the training data, but are unique instances not seen in the data source.

What makes this interesting is that cartoon characters are something we have all grown up with. We all have memories associated with Tom and Jerry or Pokemon etc. that make it easier to relate to a simpler time. Using concepts learned in class, we thought it best to recreate a version of our childhood memories. Viewing this intersection from a growth stand-point makes it seem really challenging and we all felt that this was a great use of our time. 

In class, we learned about some technical GAN approaches to generating images. For our final project, we plan to utilize some of the skills taught not to recreate classical artworks, but rather focus on generating cartoon illustrations. We want to be able to test GAN capabilities in order to see how effective it will be in generating different mediums of illustration. In addition to generating images, we will implore strategies and techniques such as inception score, nearest neighbors, and F1 score to determine the quality of the generated image.

A lot of our challenges arise from trying to work as a team in  a very uncertain time. However on the technical side, lack of knowledge in this very new field might create some interesting challenges initially. We also believe that the size of the dataset might play a part, in the sense we may not have an optimum number of images required to get the result we are aiming for, but we may try analysis on different subsets to see how our GAN behaves. Since, this is such a new topic for us, a lot of our challenges are going to revolve around finding out what our challenges would be but makes for an interesting project.
Finally, our results will be the final series of images generated as well as an analysis of the intermediate images generated throughout the generative process presented in a Jupyter notebook.

Sources we plan on using:

https://machinelearningmastery.com/how-to-evaluate-generative-adversarial-networks/

https://github.com/gsurma/image_generator

https://medium.com/@hannahfarrugia/creating-a-game-character-from-a-generative-adverserial-network-gan-fb3188af369b 

https://github.com/Zhenye-Na/pokemon-gan


## Data and Model

(10 points) 

In the final submission, this section will describe both the data you use for this project and any pre-existing models/neural nets. For each you should provide the name, a textual description, and a link. If there is a paper (for neural net) link that as well.
- Such and such Neural Net. The short description of this neural net. 
  - [link to code]().
  - [Title of Paper with Link](). 
- Training data. Short description of training data including bibliographic info. [link to data]().

## Code

(20 points)

This section will link to the various code for your project (stored within this repository). Your code should be executable on datahub, should we choose to replicate your result. This includes code for: 

- code for data acquisition/scraping
- code for preprocessing
- training code (if appropriate)
- generative methods

Link each of these items to your .ipynb or .py files within this seection, and provide a brief explanation of what the code does. Reading this section we should have a sense of how to run your code.

## Results

(30 points) 

This section should summarize your results and will embed links to documentation to significant outputs. This should document both process and show artistic results. This can include figures, sound files, videos, bitmaps, as appropriate to your generative art idea. Each result should include a brief textual description, and all should be listed below: 

- image files (`.jpg`, `.png` or whatever else is appropriate)
- audio files (`.wav`, `.mp3`)
- written text as `.pdf`

## Discussion

(30 points, three to five paragraphs)

The first paragraph should be a short summary describing your results.

The subsequent paragraphs could address questions including:
- Why is this culturally innovative?
- How does your generative computational approach differ from traditional art/music/cultural production? 
- How do your results relate to broader social, cultural, economic political, etc., issues? 
- What are the ethical concerns for this form of generative art? 
- In what future directions could you expand this work?

## Team Roles

Provide an account of individual members and their efforts/contributions to the specific tasks you accomplished.

## Technical Notes and Dependencies

Any implementation details or notes we need to repeat your work. 
- Additional libraries you are using for this project
- Does this code require other pip packages, software, etc?
- Does this code need to run on some other (non-datahub) platform? (CoLab, etc.)

## Reference

All references to papers, techniques, previous work, repositories you used should be collected at the bottom:
- Papers
- Repositories
- Blog posts

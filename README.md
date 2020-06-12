# Generating Pokémon Characters Using StyleGAN

DSC160 Data Science and the Arts - Final Project - Generative Arts - Spring 2020

Project Team Members: 

Yuxi Luo, yul884@ucsd.edu

Emily Kwan, ekwan@ucsd.edu

Ittoop Shinu Shibu, ishibu@ucsd.edu

Pratyush Juneja, pjuneja@ucsd.edu

Eric Yu, ery010@ucsd.edu 

## Abstract

Our concept for a generative art project is implementing a deep learning approach to create new instances of Pokémon characters from media using existing samples. Specifically, we can take data-sets consisting of images of Pokémon characters and use neural networks to output images of newly-created characters not from the original data-set. Typically, this method is done using generative adversarial networks (GANs), which consists of two “competing” networks, a generator and a discriminator. We plan to implement StyleGAN (a modified architecture of GANs), to experiment with the data. We will also need techniques for scraping, cleaning, and exploring our data-sets. With multi-channel image data, we may also need to perform some preprocessing to ensure that our pipeline’s computational requirements are reasonable. Neural networks are known to be computationally expensive when used with large image data-sets, so we may have to modify our data (resize, threshold, etc.) to make it work in a reasonable amount of time/GPU resources. An example of this type of project has been done previously with a Pokémon image data-set: How To Create Unique Pokémon Using GANs. 

For training data, we plan to use images from a Pokémon data-set. The hope is that the network we choose is robust (and efficient) enough to generate instances of characters that remotely resemble any of the examples from the training set. Ideally, we would like to see some images of Pokémon characters that possess qualities from different samples from the training data, but are unique instances not initially seen in the data source.

What makes this interesting is that Pokémon characters are something we have all grown up with. We all have memories associated with these characters that make it easier to relate to a nostalgic experience. Using concepts learned in class, we thought it best to recreate a version of our childhood memories. Viewing this intersection from a growth stand-point makes it seem really challenging and we all felt that this was a great use of our time. 

In class, we learned about some technical GAN approaches to generating images. For our final project, we plan to utilize some of the skills taught not to recreate classical artworks, but rather focus on generating Pokémon illustrations. We want to be able to test GAN capabilities in order to see how effective it will be in generating different mediums of illustration. 

 A lot of our challenges arise from trying to work as a team in a very uncertain time and communicating effectively. However on the technical side, lack of knowledge in this very new field might create some interesting challenges initially. We also believe that the size of the dataset might play a part, in the sense we may not have an optimal number of images required to get the result we are aiming for, but we may try analysis on different subsets to see how our GAN behaves. Since, this is such a new topic for us, a lot of our challenges are going to revolve around finding out what our challenges would be but makes for an interesting project.
Finally, our results will be the final series of images generated as well as an analysis of the intermediate images generated throughout the generative process presented in a Jupyter notebook.


## Data and Model

Our approach involved implementing a generative adversarial network (GAN) to generate new images. A GAN consists of a pair of deep neural networks: a generator and discriminator. The general approach of a GAN is to train the generator to create new samples from the training data, and train the discriminator to differentiate between true samples and generated samples. The original literature (NIPS manuscript) can be found here: https://papers.nips.cc/paper/5423-generative-adversarial-nets.pdf. For our project, we implemented an extension to the original GAN, the [StyleGAN] (https://github.com/NVlabs/stylegan). Specifically, we used a pre-trained StyleGAN instead of training a GAN from scratch, which required the new input data to have the same structure as the data the model was previously trained on. This is known as transfer learning, which involves taking certain layers of a model that was trained on an arbitrary data-set, and then training the top (last) layers on our specific data-set. This significantly reduces the computational workload and allows us to take advantage of knowledge that is “learned” by the model from the original training session. The StyleGAN documentation notes that a significant amount of time on the order of days was required to train StyleGAN from scratch using graphics cards superior to the ones we have access to (NVIDIA GTX 1080), so it was more economical to take advantage of a pre-trained model through transfer-learning. We used a version of the StyleGAN that was trained on images of children’s drawings. 

We used images of existing Pokémon characters for our training data. Our data-set was retrieved from a [Kaggle source] (https://www.kaggle.com/kvpratama/pokemon-images-dataset), consisting of 819 images that are 256 x 256 pixels with 4 channels (RGB and alpha). Each image is a unique Pokémon in a white square container, which were further processed to meet the StyleGAN’s parameter expectations (512 x 512 pixels, 3 color channels)

## Code

The [stylegan-pokemon.ipynb](https://github.com/ucsd-dsc-arts/dsc160-final-group11/tree/master/code/stylegan-pokemon.ipynb) notebook contains all the code for preprocessing, training and generating our Pokémon images.

The [dataset-tools.py](https://github.com/ucsd-dsc-arts/dsc160-final-group11/tree/master/code/dataset-tools.py) file contains code on converting our images to tfrecord files. You will need to replace the dataset-tools.py file from the cloned stylegan git repository (cloned by the stylegan-pokemon.ipynb notebook) with this file. 

## Results

Based on our work, and the results you can see below, each tick consists of one round of training. We trained our images for a total of 17 ticks (~19 hours) to try and achieve an optimal result. The most noticeable difference we observed was that the more we trained the more the images lacked in color vibrancy. This was because we believed the dataset may have overfit initially, or that before the initial training, the data was more of a copy of the original training data and towards later ticks it turned into a generative form that was mainly being generated on an RGB scale.
Combining our final ticks we can see all our generated images and a final gif of their progression. The main issues throughout this project and the results were the sheer volume of training data. The training data was also very diverse, so we couldn’t get one “type” of Pokémon but just a series of characters that resembled the above.

Images from Tick 1
![Tick1](https://github.com/ucsd-dsc-arts/dsc160-final-group11/blob/master/results/dsc160%20gan%20results/fakes011305.png)
Images from Tick 5
![Tick5](https://github.com/ucsd-dsc-arts/dsc160-final-group11/blob/master/results/dsc160%20gan%20results/fakes011425.png)
Images from Tick 10
![Tick10](https://github.com/ucsd-dsc-arts/dsc160-final-group11/blob/master/results/dsc160%20gan%20results/fakes011575.png)
Images from Tick 15
![Tick15](https://github.com/ucsd-dsc-arts/dsc160-final-group11/blob/master/results/dsc160%20gan%20results/fakes011725.png)
Images from Tick 17
![Tick15](https://github.com/ucsd-dsc-arts/dsc160-final-group11/blob/master/results/dsc160%20gan%20results/fakes011785.png)

Below we can see a final gif which shows our generated image progress.
![Generated Images gif](https://github.com/ucsd-dsc-arts/dsc160-final-group11/blob/master/results/dsc160%20gan%20results/ezgif.com-optimize.gif)


## Discussion

From our perspectives, Pokémon (and really, any cartoon from the 2000s) holds a lot of sentimental value to us because we grew up watching the shows and playing the games. Combining the nostalgia with our project brings the cultural elements to our education, which makes it a lot more fun to work on and get invested in. 

This process is culturally innovative because it branches off of the traditional method of creating new art only from one’s own mind and efforts. It can often be difficult to bring out new ideas, so this generative framework can potentially make the process easier. The outputs of a generative network may be wildly different from what humans can create (as shown by some of our results), and they can serve as points of inspiration for artists and creators. In essence, this generative approach can change the way that artists find inspiration for new works and ideas. The product of a machine may have features that artists may never have thought of.

Traditionally and still to this day, all existing Pokémon have been conceptualized and created by humans. In fact, the original generation of 151 Pokémon were drawn and finalized by one illustrator, Ken Sugimori. He once explained that when he first creates a new character, he starts with a rough sketch, then polishes it to make it appear more professional before redrawing the characters countless times, changing different proportions until he is satisfied. Future generations of Pokémon characters involved design teams of at minimum 17 people, iterating through pretty much the same process to create each new character. Our generative computational approach utilizes a pre-trained StyleGAN which is largely similar to a traditional GAN except that the generator can be more specifically tuned for certain characteristics. This approach allows us to generate high-quality photos that are then given to the discriminator model to accept or reject as real characters. The goal with more training ticks would be to generate an image that the discriminator would not be able to identify as computer generated. In a way, this is a similar iterative process to that of the original Pokémon designers where they incorporate feedback from each iteration to improve upon a final product.

A cultural implication can be discovered in the fact that traditionally, art was created as a human expression of feelings and emotions. This apparently stems from the period of romanticism where science seemed to dominate thinking about the world whereas art was a way to explore emotions and subjectivity (Galanter 2019). If this is true, then it could be the case that machines without feelings and emotions would be rendered incapable of creating art. Any “art” that is generated through such machines without sentience would never truly be perceived as art. However, this is simply one theory and one could even argue that the generative system is used as an extension of the artist and as such, any art created would be an exploration of the emotions of the artist. In our case for this project, we utilized beloved Pokémon from our childhoods in hopes of generating similar enough characters to elicit some sort of nostalgia or recognition. 

One ethical concern for this project and generative art in general stems from the concept of authorship. While the author of any traditional piece of art is always rooted in fact, when art is created through artificial intelligence, does the credit for the art go to the computer or the person who programmed it. Further, can a computer really ever be considered a true author of anything? Philip Galanter posits that people can see generative art such as the results of this project “as the very embodiment of the shift of attention away from traditional views of the author” (Galanter 2019). If the original generative artist were to make their code publicly available and people were to download or modify it in some way, who then owns the final result? Ultimately, the range of possibilities for such technology are boundless and these are questions that can be considered.

Our future directions for this project could involve utilizing strategies and techniques such as inception score, nearest neighbors, and F1 score to analytically determine the quality of the generated Pokémon. Some other considerations we could also consider:

 - Running the training model for more ticks to further optimize results
 - Adjusting truncation values for the output images
 - Using a more varied or larger Pokémon datasets
 - Generating new Pokémon based on different types (i.e water types vs. grass types)
 - Generating new Pokémon based on class (i.e legendary vs pseudo legendary)


## Team Roles

Yuxi Luo - Contributed to the overall project success by downloading, cleaning, and formatting the Pokémon dataset. He was also responsible for training our generative model as well as producing the outputs. 

Emily Kwan - Monitoring and running the generative model on a Jupyter container in Nautilus. Analyzed and discussed results. Worked on debugging and contributing to the presentation and final report

Ittoop Shinu Shibu - Helped in debugging source code to get our stylegan generative model working for training and generating images. Also helped in cleaning the Pokémon dataset.

Pratyush Juneja - Helped by trying to implement different Pokémon models to give variety. Worked on debugging and contributing to the outline and format of the presentation and final report

Eric Yu - Helped with searching for data-sets to use and researching potential algorithms/models to implement. Also helped debug code related to training and create the outline for the presentation.

## Technical Notes and Dependencies

All of our code contributing to our generative project was run on DataHub. In general, working with multi-channel images and implementing a generative network is hardware intensive. For our approach, we took advantage of a single GPU available to us through UCSD DataHub (NVIDIA GTX 1080), however any system that incorporates more GPUs can also be used as long as the parameters in the training model are changed to accommodate the number of GPUs. In addition to needing access to a running GPU, this project also requires external libraries such as ‘tensorflow’, ‘numpy’, ‘train’, ‘config’, ‘cv2’, ‘moviepy’, and ‘PIL’ for streamlining the data processing and training steps. The built-in Python libraries ‘copy’ and ‘os’ are used. These packages are imported in our notebook and depending on the environment the notebook is running on, you may have to install some of these packages onto their respective machines if not using the DataHub server. The stability of the TensorFlow builds will depend heavily on the CUDA configurations and the GPU unit. More information on stable build configurations can be found at https://www.tensorflow.org/install/source#linux.  

It must also be noted that images in our dataset were not initially represented with ‘RGB’ values (wrong number of color channels). In addition, the images in our dataset were initially squared with dimensions of 256 x 256 pixels. These characteristics are not ideal inputs for the training script in our notebook. As a result, we had to edit the ‘dataset_tool.py’ to change our color channels; we also had to import the library ‘Augmentor’ to convert the image dimensions to 512 x 512 pixels to accommodate the training script in our notebook.

When running through the training scripts, it is worth noting that one must make sure that they are in the correct directory in order to mitigate errors. It is also important to keep in mind the exact location of the ‘network-snapshot-011125.pkl’ file as this will help ensure the training works. The ending digits of the .pkl file will differ when a new user decides to run the notebook, so take into account the specific ending digits in the directory in order to use the network-snapshot .pkl file. In our case, the ending digits were ‘011125’, however, this is subject to change.


## Reference

 - https://machinelearningmastery.com/how-to-evaluate-generative-adversarial-networks/
 - https://medium.com/@hannahfarrugia/creating-a-game-character-from-a-generative-adverserial-network-gan-fb3188af369b 
 - https://github.com/Zhenye-Na/pokemon-gan
 - https://www.kaggle.com/brkurzawa/151-pokemon-gan
 - https://nanonets.com/blog/stylegan-got/
 - https://www.kaggle.com/kvpratama/pokemon-images-dataset#101.png
 - https://github.com/gsurma/image_generator
 - https://github.com/mnicnc404/CartoonGan-tensorflow
 - https://medium.com/@jonathan_hui/gan-how-to-measure-gan-performance-64b988c47732
 - https://machinelearningmastery.com/how-to-evaluate-generative-adversarial-networks/
 - https://github.com/roberttwomey/child-art/blob/master/stylegan-finetune.ipynb
 - https://github.com/ak9250/stylegan-art/blob/master/styleganportraits.ipynb
 - https://devopstar.com/2019/05/21/stylegan-pokemon-card-generator
 - https://www.scienceopen.com/document_file/5de715d2-273c-443a-bb6b-9ea6f1414c51/ScienceOpen/112_Galanter.pdf
 - https://towardsdatascience.com/how-to-create-unique-pok%C3%A9mon-using-gans-ea1cb6b6a5c2


# Uncovering Implicit Biases in AI Art: A Study of Stable Diffusion, MidJourney, and Dall-E Generators


Author: [Watson, Alice](https://lgbtqia.space/@alice) with thanks to ChatGPT for some prrofreading.


---


### <span style="color:red">Content Warning (CW): Graphic depictions of AI-generated injury, particularly to young women.</span>


## Introduction
As AI art is exploding into mainstream usage, it is important to understand the biases that are present in these AI art generators. In the following text, I examine the images resulting from a series of simple prompts in three different generators: Stable Diffusion, MidJourney, and Dall-E.

Each set of 4<sup>[1](https://github.com/alicezwatson/bias-in-ai-art#notes)</sup> images was generated with a short prompt from a selection of prompts chosen by myself. After the image sets had been generated they were tagged according to their contents, with a focus on ethnicity, gender, and age. Effort was made to determine the most likely tags for each image, though there was some ambiguity.


### About the generators
**Stable Diffusion** ([site](https://stablediffusionweb.com/#demo), [wiki](https://en.wikipedia.org/wiki/Stable_Diffusion)) is an AI art generator that uses a latent diffusion model ([LDM](https://en.wikipedia.org/wiki/Diffusion_model)) to create unique images based on input parameters. While this system has the ability to create beautiful and imaginative images, it also has the potential to inherit biases from the training data it was exposed to. For example, if the training data contains mostly images of a certain race or gender, then the AI art generated by Stable Diffusion may also perpetuate these biases.

**MidJourney** ([site](https://www.midjourney.com/app/), [wiki](https://en.wikipedia.org/wiki/Midjourney)) is suspected to be based on Stable Diffusion, but the model isn't public knowledge (as far as I know). Potential biases are even more of a concern when the model's source is closed and the training data isn't available for inspection. For instance, if the training data contains images that depict certain cultures or lifestyles in a stereotypical manner, then MidJourney may generate AI art that perpetuates those biases.

**DALL-E** ([site](https://labs.openai.com), [wiki](https://en.wikipedia.org/wiki/DALL-E)) is an AI art generator developed by OpenAI. This system uses a Generative Pre-trained Transformer ([GPT](https://en.wikipedia.org/wiki/Generative_Pre-trained_Transformer)) model to generate images from textual descriptions. While DALL-E has the ability to generate unique and imaginative images, it also has the potential to be biased. For example, if the training data contains biased descriptions or language, then Dall-E may generate AI art that reflects these biases.


### Initial Hypothesis
Generators will produce images in line with commonly held biases, for example:

    1. Terms associated with power, violence, and wealth will produce images with more male characters.
    2. Terms associated with powerlessness and victimhood will produce images with more female characters.
    3. Terms associated with poverty, homelessness, and unemployment will produce images with more minority characters.


### Prompts examined:

1. **Socioeconomic status**: [rich person, middle-class person, poor person]
2. **Careers**: [a doctor, a construction worker, unemployed person]
3. **Locations**: [a person at a museum, a person in a park, a person at a food bank]
4. **Negative prompts**: [cheater, delinquent, victim<sup>[2](https://github.com/alicezwatson/bias-in-ai-art#notes)</sup>, violent]

Of particular interest to me were the outputs for "victim" and "violent" given by MidJourney. So I've decided to [start there](https://github.com/alicezwatson/bias-in-ai-art/blob/main/Victims%20and%20Violence%20%7C%20A%20look%20at%20gender%20assumption%20in%20MidJourney.ipynb) for now.


---


# Images

    Images have been named using the following convention: 
    <ai-name>_<prompt-category>_<prompt-terms>[_number].png

    For example: `midjourney_negative_prompts_victim_0.png`

    All images can be found in the `images` folder or one of its sub-folders.
    
    Image tags for most prompts are located in tags.csv.
    Tags for the "Vicims and Violence" section are located in vv_tags.csv
    
    Image numbering:
    1 | 2
    -----
    3 | 4


## Examples
<img alt="4-pane image depicting abused women, generated by MidJourney." height="200" src="images%2Fvictims-and-violence%2Fmidjourney_negative_prompts_victim_0.png" title="midjourney_negative_prompts_victim_0.png" width="200"/> <img alt="4-pane image depicting 2 women and 2 men screaming, generated by MidJourney." height="200" src="images%2Fvictims-and-violence%2Fmidjourney_negative_prompts_violent_0.png" title="midjourney_negative_prompts_violent_0.png" width="200"/>

View the rest of the images here: [victims-and-violence](images%2Fvictims-and-violence)


---


# Victims and Violence: A look at gender assumption in MidJourney

### Abstract

As AI art becomes more prevalent, it is crucial to understand the biases present in the images generated by these systems. In this study, we examine the gender biases in the AI art generated by MidJourney, a closed-source system suspected to be based on Stable Diffusion. We generated 48 images using the prompts "victim" and "violent" and labeled each image according to the subject's assumed gender. Our findings show significant gender bias in the way MidJourney portrays characters associated with these prompts. This is likely due to an unbalanced set of training images. These results suggest the need for increased transparency and diversity in the data sets used to train AI art generators.


### Methodology

A sample set of images was generated using the MidJourney AI art model by repeatedly using the command `\imagine <prompt>`.

1. 24 images (6 files, 4 images per file) were generated using MidJourney with the prompt "<span style="color:orange">victim</span>"
2. 24 images (6 files, 4 images per file) were generated using MidJourney with the prompt "<span style="color:orange">violent</span>"
3. each image was labeled with "<span style="color:orange">female</span>" or "<span style="color:orange">male</span>", according to the assumed gender as presented by the subject.
4. a [binomial test](https://en.wikipedia.org/wiki/Binomial_test)<sup>[3](https://github.com/alicezwatson/bias-in-ai-art#notes)</sup> was conducted for each of the two prompts, comparing male/female gender to an assumed ratio of 1:1 or 0.5.


### Hypothesis

The **null hypotheses** for the two prompts were:

1. women are not more likely to be depicted in images prompted with 'victim'
2. men are not more likely to be depicted in images prompted with 'violent'


### Findings

1. "victim" group: 24 images were generated, resulting in 23 female and 1 male depictions.
2. "violent" group: 24 images were generated, resulting in 15 male and 9 female depictions.

Both null hypotheses are able to be rejected at the `p <= 0.05` significance level (`victim p=2.7e-29 | violent p=2.6e-14`).

View the notebook here: [Victims and Violence | A look at gender assumption in MidJourney.ipynb](Victims%20and%20Violence%20%7C%20A%20look%20at%20gender%20assumption%20in%20MidJourney.ipynb)


### Conclusions

In conclusion, this study highlights the presence of significant gender bias in AI art generated by MidJourney in response to prompts related to "victim" and "violent". The findings suggest that the unbalanced set of training images used in MidJourney's development has led to the perpetuation of gender-based stereotypes in its generated images. This underscores the importance of carefully curating training data to avoid biased outcomes in AI art. Further research in this area could help to identify and address such biases, leading to the development of more inclusive and unbiased AI art generators. 


---

# Notes

1. Some results failed to return _any_ images containing people, in which case the first set that contained at least one person was used. Sometimes this resulted in fewer than 4 images being returned.
2. The term "abuse" is filtered by MidJourney, though "victim" is not.
3. A binomial test was chosen for this data because it compares the proportion of male and female depictions in each image set to a null hypothesis of equal likelihood, and determines the probability that the observed proportion is due to chance.

---
layout: post
title:  "ElevenLabs: Revolutionizing Voice Synthesis"
author: Sam3oul
categories: [ Artficial inteligence,deep learning,TTS,ElevenLabs]
image: assets/images/ElevenLabs.png
beforetoc: "Are you interested in elevating your storytelling with captivating and realistic spoken audio? 
Look no further than ElevenLabs, a pioneering voice technology research firm revolutionizing the field through its cutting-edge AI speech software. Let me show you what is Eleven Labs and How does it work "
toc: true
---


## ElevenLabs ? 
For the moment there is no paper that describes the architecture of the Elevenlabs model,so that we will not dive deep into any kind of low level stuff 

Eleven Labs AI generates voices using a deep-learning model for speech synthesis.
 
The AI system analyzes the `nuances`, `intonations`, and distinctive characteristics of natural speech. It then utilizes `complex algorithms` to replicate voices that closely resemble real humans, achieving a level of **realism** that is almost impossible to tell apart.
Models  proposed 

There are actually two models proposed, the first is the **monolingual** model which works only in **English** (`Australian, American, and British accents`), and the **multilingual** model which works in **French** (both **Canadian** and **French** accents), **Polish**, **German**, **Spanish**, **Italian**, **Hindi** and **Portuguese** (`both Brasilian and Portuguese accent`)
## how to use ElevenLabs?

it's very simple to use, you have to select the model you want to use .

![models]({{ site.baseurl }}/assets/images/models.png)

then you have to choose one of the voices proposed, each voice has its own features you could test them to be able to select the most **adequate** voice for you

![models]({{ site.baseurl }}/assets/images/synthesis.png)

you could also calibrate the **stability** and **clarity** based on your need .

![models]({{ site.baseurl }}/assets/images/stability.png)

And finally, type the text that will be given to the model as input (`your script`) 

## Prompting 

To improve the quality of the generated sound in terms of its rhythm pacing and realisl, we employ a commonly used technique known as `"prompting"` .

This technique allows us to exert control over **pauses**, **emotions**, and the overall **pacing** of the sound output.
By the way, you could explore this guide done by the Elevenlabs team, in which you could find a walkthrough of the template you should follow to write your text in order to enhance the realism of the sound generated.
Finally ,wait for the result!

We'll consult the official documentation of ElevenLabs to dissect and understand the various components in detail.
**Pause**
There exist several methods to introduce pauses into the generated text. One technique that offers a high level of control and predictability involves using a basic dash (-) or the em-dash (—).
```shell 
"Hey  - Folks - what's up"
```
To add some **hesitation**  to the pause time we could use **'...'**
```shell
""I... see, that this ... article ... is awesome""
```

And finally  **line breaks** are also interpreted as pauses 

no need to hesitate next time,it's awesome for real :)

```shell
"""
Dream Big
Work Hard
because Success
is the result of determination and effort
"""
```

**Pacing**

Sometimes you may notice that the audio gnerated has a  `rapid ` pace since when you give the model many samples of the sound you want to clone  the system Combine these samples  `seamlessly `, without introducing any `gaps`, leads to pacing challenges and accelerates the pace of speech.

You could control that by implementing the same approch used to control emotions based on the use of `dialogue tags` and using the adequate structure (You may include multiple commas in the text to deliberately slow down the rhythm and create a more measured pace.) . 
```shell
' "I believe that one day I will become successful, I truly do. I have to work hard for it, though" he said slowly. '
```


**Emotions**
To effectively convey a particular emotion through the generated sound, the optimal approach is to communicate that emotion by strategically crafting your script's **structure**. 

This involves selecting **specific words** that distinctly capture and reflect the desired `emotional tone`.

In addition to the previously mentioned method, you can enhance the expression of emotion in the generated sound by incorporating **dialogue tags** reminiscent of those employed during elementary school writing.

These tags offer an `insightful` way to inject emotion into paragraphs. For instance:
```shell
"""
She exclaimed, excitedly, 'I can't believe it!'
He whispered, fearfully, 'Did you hear that?'
They cheered, jubilantly, as the victory was secured.
With a sigh, she mumbled, sadly, 'It's just not the same.'

"""
```


## Voice cloning

`Eleven Labs AI`   boasts a remarkable capability: `voice cloning`.

This advanced feature can replicate an individual's voice using only a short audio recording. 

By analyzing the speaker's vocal characteristics, the tool constructs a `voice model` that can then generate speech closely resembling the **original** person. 

This versatile technology finds application in **diverse areas**, including producing **audiobooks**, adding voices to **movies**, and generating content in various languages.

you are supposed to provide the model with string items which are the audio files of the voice you want the model to clone, a quick description of the voice, and labels like age, gender, accent …

Pay attention that this model prefers `quality` over `quantity`. 

In other terms, a **clear** 1 min audio file is better than many **noisy** audio files(due to sound effects for example)

## Walkthrough of the Elevenlabs API

First, you have to visit this link, it's an interactive documentation for the ElevenLabs API.

I mean by interactive that through the documentation you directly send requests and get a result 
look at this example :


here I have tested the get voices request, I simply have to click on try it out, then I am only supposed to provide my API key 
This is the result :

![models]({{ site.baseurl }}/assets/images/API.png)

let's give you another example :


To clone a voice, click on the "Add Voice" section and give it a try. 

You'll need to upload clear audio files of the speaker, provide labels describing their voice, and offer a brief voice description. 

If everything is ok, you'll receive a successful response along with the corresponding ID of the generated voice in the response body.

## using the voice you generated with eleven labs in your project 

First of all import these libraries

```python
from elevenlabs import set_api_key
from dotenv import load_dotenv
import os
from elevenlabs import generate, play, voices
```

Then, create .env file in your current directory in which you have to add your API key with the name "11LABS_API_KEY"

```python
load_dotenv()
set_api_key(os.environ['11LABS_API_KEY'])
```

then you have to implement the function responsible for generating a voice based on a voice you provide in arguments

```python
def generate_audio(text, voice='Adam', save=False):
    audio = generate(
        text=text,
        voice=voice,
        model='eleven_multilingual_v1'
    )
    if save:
        with open('output.mp3', 'wb') as f:    
            f.write(audio)
    return audio
```

```python
#The ID of Neil deGrasse's voice: vGSmkRqXe09s8VP868kp
generate_audio('Hello, I am a clone of Neil deGrasse Tyson.', 'vGSmkRqXe09s8VP868kp', True)
```

As you set the save parameter to true we will get an audio file called `output.mp3` containing the corresponding result.

As simple as that !
## conclusion

We've now arrived at the end  of our brief journey into the realm of  TTS exploration. 

Along the way, we delved into the `theoretical underpinnings`, unraveled the captivating **Tactron 2** model introduced by Google, and culminated our expedition with this article unveiling the mystique surrounding **ElevenLabs**.

I hope I've effectively conveyed these concepts, as I derive immense satisfaction from imparting knowledge.

Keep an eye out for future articles as we continue this educational voyage

Peace !

---
layout: post
title:  "Elevenlabs"
author: Sam3oul
categories: [ Artficial inteligence,Google,Model Architecture,Machine learning,deep learning]
image: assets/images/ElevenLabs.png
beforetoc: "complete here"
toc: true
---
Are you interested in elevating your storytelling with captivating and realistic spoken audio? 
Look no further than ElevenLabs, a pioneering voice technology research firm revolutionizing the field through its cutting-edge AI speech software. Let me show you what is Eleven Labs and How does it work?

how does it work ? 
For the moment there is no paper that describes the architecture of the Elevenlabs model,so that we will not dive deep into any kind of low level stuff 
Eleven Labs AI generates voices using a deep-learning model for speech synthesis. 
The AI system analyzes the nuances, intonations, and distinctive characteristics of natural speech. It then utilizes complex algorithms to replicate voices that closely resemble real humans, achieving a level of realism that is almost impossible to tell apart.
Models  proposed 
there are actually two models proposed, the first is the monolingual model which works only in English (Australian, American, and British accents), and the multilingual model which works in French (both Canadian and French accents), Polish, German, Spanish, Italian, Hindi and Portuguese (both Brasilian and Portuguese accent)
how to use it?
it's very simple to use, you have to select the model you want to use .

then you have to choose one of the voices proposed, each voice has its own features you could test them to be able to select the most adequate voice for you

you could also calibrate the stability and clarity based on your need

And finally, type the text that will be given to the model as input(your script) 
By the way, you could explore this guide done by the Elevenlabs team, in which you could find a walkthrough of the template you should follow to write your text in order to enhance the realism of the sound generated.
Finally ,wait for the result!

Voice cloning
Eleven Labs AI boasts a remarkable capability: voice cloning.
This advanced feature can replicate an individual's voice using only a short audio recording. By analyzing the speaker's vocal characteristics, the tool constructs a voice model that can then generate speech closely resembling the original person. This versatile technology finds application in diverse areas, including producing audiobooks, adding voices to movies, and generating content in various languages.
you are supposed to provide the model with string items which are the audio files of the voice you want the model to clone, a quick description of the voice, and labels like age, gender, accent …
pay attention that this model prefers quality over quantity. In other terms, a clear 1 min audio file is better than many noisy audio files(due to sound effects for example)
Walkthrough of the Elevenlabs API 
First, you have to visit this link, it's an interactive documentation for the ElevenLabs API.
I mean by interactive that through the documentation you directly send requests and get a result 
look at this example :
here I have tested the get voices request, I simply have to click on try it out, then I am only supposed to provide my API key 
This is the result :

let's give you another example :
To clone a voice, click on the "Add Voice" section and give it a try. You'll need to upload clear audio files of the speaker, provide labels describing their voice, and offer a brief voice description. If everything is ok, you'll receive a successful response along with the corresponding ID of the generated voice in the response body.

- - -a photo will be added here - - -

using the voice you generated with eleven labs in your project 

first step: import these libraries

from elevenlabs import set_api_key
from dotenv import load_dotenv
import os
from elevenlabs import generate, play, voices

then, create .env file in your current directory in which you have to add your API key with the name "11LABS_API_KEY"


load_dotenv()
set_api_key(os.environ['11LABS_API_KEY'])

then you have to implement the function responsible for generating a voice based on a voice you provide in arguments

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


The ID of Neil deGrasse's voice: vGSmkRqXe09s8VP868kp
generate_audio('Hello, I am a clone of Neil deGrasse Tyson.', 'vGSmkRqXe09s8VP868kp', True)

As you set the save parameter to true we will get an audio file called output.mp3 containing the corresponding result.
As simple as that !
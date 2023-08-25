---
layout: post
title:  "Deep dive into TTS"
author: Sam3oul
categories: [ Artficial inteligence, tutorial ]
image: assets/images/18.jpg
---
This is a walk through the steps that enable us to generate voice based on a given text
What is TTS? 
Text-to-speech (TTS) stands as a captivating technology that converts written text into spoken language. This innovation enables computers and devices to interact audibly with users, seamlessly turning written information into speech that sounds completely natural.
 The potential of TTS knows no bounds: from enriching accessibility for those with visual impairments to crafting captivating voice-overs for multimedia content.
Utilizing advanced algorithms and linguistic models, TTS systems normalize, analyze input text, utilize methods to synthesize speech, and generate audio output that skillfully replicates human speech patterns, intonation, and even emotions.
In the field of Text-to-Speech (TTS) solutions, diverse companies offer tools. Amazon's Polly provides lifelike voices with customization, Google's Text-to-Speech employs deep learning for natural speech synthesis, and Microsoft's Azure Cognitive Services offers cloud-powered voice customization. These solutions reflect technological innovation, catering to a wide array of applications and showcasing the dynamic evolution of the TTS landscape.
TTS's subtasks 
generating speech from text is essentially based on 2 main subtasks :
the first subtask is Mel-Spectrogram prediction which is a technique commonly used in audio processing, particularly in TTS and ASR( Automatic Speech Recognition) that aims to predict the mel-spectrogram representation of an audio signal, before we go further let's break down some terms :
Mel-Spectrogram 
it is a visual representation of the frequency content of an audio signal over time. It is obtained by taking the Short-Time Fourier Transform (STFT) of the audio signal and then mapping the resulting frequency bins onto the Mel scale, which is a scale that better represents the way humans perceive differences in pitch.
Mel-spectrograms are widely used in speech and audio analysis because they capture the signal's frequency and time-domain information.

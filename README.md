# Chatbot

## Summary
This project is something that I have wanted to work on for a while. AI and Chatbots companions/assistants are a huge staple of sci-fi media, and I've always wanted to try my hand at making one of my own. Especially right now during the "AI" gold rush as resources and 
support available have never been more accessible. This project was made with customizability in mind, a generic skeleton that can be configured in several different ways for the benefit of the user according to things such as preferences and/or available hardware. The 
project mainly leverages Google Colabs free available T4 GPU, but can be run locally as a notebook through something like Jupyter Notebook. 

The actual "brain" component of the Chatbot is the LLM, of which there are 4 potential options available, each with their own pros and cons. For more information, refer to the starter Colab linked, wherein all are listed in each section. To briefly summarize the options 
available are leveraging OpenAI's ChatGPT to "mimic" the character you want it to play, via prompts and telling it all the details it needs. The next is leveraging Character.AI's bots, where you can either use a pre-existing bot or create your own; similar to ChatGPT where 
you will have to fill in prompts while creating to "tell" it how to act and behave. The next is fine-tuning an LLM yourself, in this case Falcon-7B, and using a dataset of your characters prompts and responses to train it to behave that way. The final way is leveraging 
LLM-Engine and Scale for the same thing, but with access to more models besides Falcon-7B.

Besides this there are other different features. You can "speak" to it via the Speech to Text modules, wherein your real time live voice data will be converted to text data that it will read and respond to. Then there's also the Text to Speech module, where you can get the
LLM to "speak" to you, where it's text response will be converted to audio, using either a standard mechanical voice, or a deepfake voice mimic. Finally there's also the Face component, where a face, that you provide, can be provided to the faceless machine for the added
touch, where it will either respond in gif form or with a deepfake face.

Usage is as listed below.

WARNING: It goes without saying that this is not made for and should not be used for malicious purposes. Deepfaking anyones voice and face for purposes of profit, humiliation, extortion, etc carries strict legal ramifications. This is made for harmless personal aforementioned
uses (i;e assistant). 


## Usage


## In-Progress
1. 100% Local compatibility; certain features such as face and voice deepfaking is not currently configures for Local use
2. Further optimize for speed and memory
3. Account for and implement safeguards against version updates potentially deprecating and/or removing certain functions 


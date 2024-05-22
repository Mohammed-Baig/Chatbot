# Chatbot
[![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/drive/1Oauo2m8-M0yCp0vSUKkCdAzKqw21R-3T?usp=sharing)

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

If this is your first time, go through each step in order and make sure to run all the cells of your chosen path. To change paths in a step/component, run the cells in that path to override your current choice and set your new one. 

### Speech to text
There are two options for input, either text or voice. If you want to type feel free to skip this part. If you do want to speak though, you have two options, one if you're running the machine locally, appropriately labeled "Local" and one for Google Colab, labeled
"Colab Version." Run the one that corresponds to the Notebook you're running this on. If you're running locally make sure the function is using the right device_index as source from the previous cell.

### Text to Speech
There are two options for output same as the input, text or voice. If you're okay with reading the chatbot response feel free to skip this part. If you want to have it spoken then again you have two options, you can either run the Tacotron Model, or the standard Google
Translate TTS, the pros and cons of which are listed in the notebook for you to read and make your decision on. For Tacotron when you run the cells you will eventually be prompted to insert clean audio clips in wav format. The output will be better depending on the duration, amount, and quality of your audio clips. The Google Translate TTS has no such requirements and can be run as-is. Pick the one you want.

### Face Component
Note: If you want to run either of the Face Component options, you will need to run either of the Text to Speech options. For this part you have two options, either a GIF face, or a deepfake generator. For the GIF you will need three images of your characters face, 
preferably the first one closed mouth, the second semi open, and the third fully open. Upload these three directly to /content in your current Colab session first and run the GIF cells. For the deepfake you will need just one face. After you run the first three cells, all the import ones, you will navigate to the SadTalker/examples/source_image/ folder and insert your file as a PNG. Then run the cell, select your image, and proceed as normal. 

### LLM
Here you have four options:
#### GPT-3
Run the Imports, and then, whether you want to type in your input or speak it, run the appropriate Main cell. You will need to paste in your API-key and in the "content" the details of how the "system" should behave. Make sure to comment out the output you don't want,
either text if you want it spoken(make sure for this that you ran the Text to Speech component from above), or the TTS if you want the output to be readable text.

#### Character.ai
You will need a Character.ai account to use this part so make sure to have one created and to have a username ready on hand. Run the Install like normal and then get to Main, where you have the three main options listed out to you. Select the one you want, making sure to choose the face one that corresponds to the option you choose back in Face Component. Otherwise if you didn't run the Audio Input and Output option, commenting out correct input/output line based on whether you want those input/output options or not(audio or text). In all three cases you will need to paste in your username, the owner_id, char_id, and room_id. room_id can be set as "TiqLm-------------", char_id can be found according to the instructions outlined here: https://pycai-two.gitbook.io/pycai2/getting-information, and owner_id requires you to navigate to the chat page for your character on the OLD char.ai site, open up inspect element and devtools, navigate to storage > local storage, search for char_token, and copy paste that value in. Finally, if you're using GIF, you will need to paste in the name of the three images you should have uploaded to the project.

#### Local model
For this, assuming it is your very first time, you will need a couple of things. Firstly you'll need training data, the reference and format can be found in the LLM Training Formats > Local Train folder of this repo. Naturally the more data you have the better the fine tune will be. Next you will need a Write key for HuggingFace. Once you have these upload your training data csv file to the project and navigate to Train new model Run the imports, and use your key at the very end. Run Load Model, then when you get to Prepare dataset, make sure to type in your uploaded training data name into the proper place, then run as normal until you reach Save the model. Here, make sure to properly name what you would like to save this fine tuned model as, as this will be what you will be running later.

Now that you have a trained model, or assuming you had one from the start, navigate to Run Trained Model. Run the imports section as usual, then once you reach Run the model, make sure to type in the name of the model you would like to use in PEFT_MODEL; ideally the same one you trained from the previous step unless you have another you'd like to try. Once you have these cells run and you reach the three options, make sure to pick the one that best suits you. Remember that you will need the proper prerequisites, that in the GIF option you will need to type the names of all three face image files, and that for Audio Input and Output, to comment out the correct input/output line based on whether you want those input/output lines or not(audio or text).

#### LLM-Engine
For the final option, you will again need training data, similar to the last step. To see how that should be formatted, refer to LLM Training Formats > LLM-Engine in this repository. Then again upload that file to the session storage. Then in Train new model, at the very end of the imports section, make sure to type in your api key. You can find that documentation source link. Type the name of that file into the first cell of Training into the correct spot and run. Once you have the "id", copy paste that value into the next cell, alongside the suffix of what you'd like the file to be named, and the name of the model. You can find the full list of fine-tune ready models available on the aforementioned documentation source link. Run that cell and get the response, then paste the response into the appropriate line in the next cell and run as normal. Once you've done this run the next line to get the full list of names of models you've fine tuned. You will use these in the next part.

Once again run Imports as normal, paste your API key into the right spot, and get the name of the model you'd like to use. Then in Main code choose the option that you want, making sure to paste in the proper name of the model you're running into right spot, making sure to write the name of the three images for the GIF call if you're using that, and commenting out correct input/output line based on whether you want those input/output options or not(audio or text)

## In-Progress
1. 100% Local compatibility; certain features such as face and voice deepfaking is not currently configures for Local use
2. Further optimize for speed and memory
3. Account for and implement safeguards against version updates potentially deprecating and/or removing certain functions 

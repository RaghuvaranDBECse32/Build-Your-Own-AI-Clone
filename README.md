## Google Colab Notebook

Here is link of [Google Colab Notebook](https://colab.research.google.com/drive/1OGkiAZsYfShY0o8ZphCUuXkmb2Om422X?usp=sharing)

* This Notebook Contains - 
    * Data Collection From Whatsapp
    * Data Prepration
    * Data Filtering
    * Model Training
    * Inference
    * Saving Finetuned Model
    * GGUF Conversion
    * Downloading Saved Model


## Chatting With Fine-Tuned Model Using Ollama (You can also use [LM Studio](https://lmstudio.ai/) & [GPT4ALL](https://www.nomic.ai/gpt4all))

### Downloading Ollama
Go to the [downloads page of Ollama](https://ollama.com/download) and download and install it according to your OS.

### Loading the Model into Ollama
1. Open your file manager.
2. Navigate to the directory where you have downloaded the fine-tuned model, generally the Downloads folder.
3. Right-click anywhere on the screen and choose "Open terminal here." If you are using Windows, you can directly type `cmd` into the address bar and hit enter.
4. Type `ollama --version` into the terminal to check if you have installed Ollama successfully.
5. Make sure the model `unsloth.Q8_0.gguf` and `Modelfile` are in the current directory.
6. Open `Modelfile` using any text editor.
7. Edit the first line to ensure it looks like `FROM ./unsloth.Q8_0.gguf`, and save it.
8. Type this command: `ollama create my_model -f Modelfile`. This will add the model into Ollama.
9. Now type `ollama run my_model`.
10. You can now chat with your model.

## Using Model to Automate WhatsApp
Here comes the final part. I am using this wonderful tool [WPP_Whatsapp](https://github.com/3mora2/WPP_Whatsapp) to automate WhatsApp. By using this, we can use our model to respond to any incoming messages on WhatsApp. We can define specific people to talk to. Here is the step-by-step guide:

1. Clone this repo using:
    `git clone https://github.com/Eviltr0N/Make-AI-Clone-of-Yourself.git`

2. Go to the cloned repo:
    `cd Make-AI-Clone-of-Yourself/`

3. Install all the required packages by:
    `pip install -r requirements.txt`

4. First run:
    `python3 chat.py`

   Then type something like "Hello" and hit enter. If it works, it means everything is set up correctly.

5. Exit by pressing `Ctrl+C`.
6. Now run:
    `python3 ai_to_whatsapp.py`

7. It will take a bit of time at first to download the Chromium browser. As it finishes, a browser window will appear, and you have to scan the QR code using WhatsApp to link your WhatsApp account.
8. Switch back to the terminal. You have to provide the phone number of the other person you want to respond to with this AI model.
9. The phone number must include the country code without the `+` symbol, such as `916969696969`, then press enter.
10. As soon as that person sends any message, it will be printed on the terminal, and the AI model will respond to it.

### Keep in Mind
* If you want to change the temperature and top_k of the model (in simpler terms, temperature means creativity of the model), then:
    1. Open the `ai_to_whatsapp.py` file using any text editor.
    2. Go to the 9th line where you will find:
       `my_llm = LLM("my_model", 0.3, 50, 128)`

    3. Change `0.3` to a higher value such as `0.9` to increase the temperature (creativity) of the model.
    4. You can also change top_k from `50` to a higher value like `95`.

* Temperature can vary from `0.1` to `1` and top_k from `1` to `100`. The higher the temperature, the more creative and unpredictable the model becomes.
* Keep playing with the values of `temperature` and `top_k` until you are satisfied with the model's responses.


## What's Next
* Adding multimodal capabilities so this can understand and react to images too, as it currently supports only text messages.

* Adding some sort of agent pipeline above this model so another model, such as `LLaMA 3.1`, can see the message and the response of this model and judge if it is suitable or not, and can modify the model response accordingly.

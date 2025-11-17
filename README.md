## Name: Jeffy Brailin T
## Reg.No: 212223040076

## Development and Deployment of a 'Chat with LLM' Application Using the Gradio Blocks Framework

### AIM:
To design and deploy a "Chat with LLM" application by leveraging the Gradio Blocks UI framework to create an interactive interface for seamless user interaction with a large language model.

### PROBLEM STATEMENT:
Building a user-friendly application that allows seamless interaction with a large language model (LLM) is challenging without requiring specialized API keys or external resources. This project addresses the need for an accessible, open-source solution to implement such applications using pre-trained models and the Gradio Blocks framework.

### DESIGN STEPS:

#### STEP 1:
Import Required Libraries. Install and import the necessary libraries: Gradio for the UI.
Transformers for using pre-trained models.

#### STEP 2:
Use a pre-trained model like GPT-2 or DialoGPT from Hugging Face.Initialize the model using the pipeline API for straightforward interaction.

#### STEP 3:
Create a function to: Process user input. Pass it to the language model.Return the generated response.Design the user interface using Gradio Blocks, adding components for input, output, and interactivity.

#### STEP 4:
Run the application locally with demo.launch(). Optionally deploy it to the cloud for broader accessibility.

### PROGRAM:

```
import gradio as gr
from transformers import pipeline

# Load a pre-trained LLM from Hugging Face
chat_model = pipeline("text-generation", model="gpt2", max_length=200)

# Define the function to interact with the LLM
def chat_with_llm(user_input):
    try:
        # Generate a response
        response = chat_model(user_input, max_length=150, num_return_sequences=1)
        return response[0]['generated_text']
    except Exception as e:
        return f"Error: {str(e)}"

# Design the Gradio Blocks UI
with gr.Blocks() as demo:
    gr.Markdown("# 🤖 Chat with LLM")
    with gr.Row():
        with gr.Column():
            user_input = gr.Textbox(label="Enter your query:", placeholder="Type your message here...")
            submit_button = gr.Button("Submit")
        with gr.Column():
            response_output = gr.Textbox(label="LLM Response:", lines=10, interactive=False)
    
    # Add functionality
    submit_button.click(chat_with_llm, inputs=[user_input], outputs=[response_output])

# Run the application
demo.launch()


```


### OUTPUT:
<img width="1084" height="559" alt="image" src="https://github.com/user-attachments/assets/3dcd60a7-430a-4915-b056-8d2a4426ef62" />

### RESULT:
Thus the Chat with LLM Application Using the Gradio Blocks Framework is created successfully.

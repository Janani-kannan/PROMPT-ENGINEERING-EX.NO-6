# Ex.No.6 Development of Python Code Compatible with Multiple AI Tools

# Date: 27/03/2026
# Register no: 212224230102

# Aim

To write and implement Python code that integrates with multiple AI tools to automate API interaction, compare outputs, and generate actionable insights using different AI models.

# Objective

The objective of this experiment is to:

Connect Python with multiple AI APIs.
Send the same prompt to different AI tools.
Compare generated outputs.
Analyze quality, accuracy, and response depth.
Use the Persona Pattern as a programmer for a specific application area.
AI Tools Used
OpenAI ChatGPT API
Google Gemini API
Hugging Face Inference API
Persona Pattern Used
Persona:

Cybersecurity Programmer

The AI model is instructed to behave like:

A cybersecurity expert
A Python programmer
A reverse engineering assistant

This persona helps generate more technical and domain-specific responses.

# Problem Statement

Develop a Python program that:

Sends prompts to multiple AI APIs.
Receives responses automatically.
Compares outputs.
Generates insights based on:
Accuracy
Technical depth
Clarity
Response quality
## Python Code

```
import requests
import json

# -----------------------------
# API Keys
# -----------------------------

OPENAI_API_KEY = "YOUR_OPENAI_API_KEY"
GEMINI_API_KEY = "YOUR_GEMINI_API_KEY"
HF_API_KEY = "YOUR_HUGGINGFACE_API_KEY"

# -----------------------------
# Persona Prompt
# -----------------------------

prompt = """
You are a cybersecurity programmer and reverse engineering expert.
Explain how malware analysis is performed using Python tools.
Include:
1. Static Analysis
2. Dynamic Analysis
3. Tools Used
4. Safety Precautions
"""

# -----------------------------
# OpenAI API Function
# -----------------------------

def get_openai_response(prompt):
    url = "https://api.openai.com/v1/chat/completions"

    headers = {
        "Authorization": f"Bearer {OPENAI_API_KEY}",
        "Content-Type": "application/json"
    }

    data = {
        "model": "gpt-4o-mini",
        "messages": [
            {"role": "user", "content": prompt}
        ]
    }

    response = requests.post(url, headers=headers, json=data)

    return response.json()["choices"][0]["message"]["content"]

# -----------------------------
# Gemini API Function
# -----------------------------

def get_gemini_response(prompt):

    url = f"https://generativelanguage.googleapis.com/v1beta/models/gemini-pro:generateContent?key={GEMINI_API_KEY}"

    headers = {
        "Content-Type": "application/json"
    }

    data = {
        "contents": [
            {
                "parts": [
                    {"text": prompt}
                ]
            }
        ]
    }

    response = requests.post(url, headers=headers, json=data)

    result = response.json()

    return result["candidates"][0]["content"]["parts"][0]["text"]

# -----------------------------
# Hugging Face API Function
# -----------------------------

def get_huggingface_response(prompt):

    API_URL = "https://api-inference.huggingface.co/models/gpt2"

    headers = {
        "Authorization": f"Bearer {HF_API_KEY}"
    }

    payload = {
        "inputs": prompt
    }

    response = requests.post(API_URL, headers=headers, json=payload)

    return response.json()

# -----------------------------
# Execute AI Models
# -----------------------------

print("Generating responses...\n")

openai_output = get_openai_response(prompt)
gemini_output = get_gemini_response(prompt)
hf_output = get_huggingface_response(prompt)

# -----------------------------
# Display Outputs
# -----------------------------

print("===== OpenAI Response =====")
print(openai_output)

print("\n===== Gemini Response =====")
print(gemini_output)

print("\n===== Hugging Face Response =====")
print(hf_output)

# -----------------------------
# Simple Comparison Logic
# -----------------------------

print("\n===== ANALYSIS =====")

if len(openai_output) > len(gemini_output):
    print("OpenAI generated a more detailed response.")
else:
    print("Gemini generated a more detailed response.")

print("Hugging Face output may require further fine-tuning.")
```
## Explanation of the Code
Step 1: Import Libraries

The program imports:

requests → for API communication
json → for handling JSON responses
Step 2: Define API Keys

Each AI tool requires its own API key for authentication.

Step 3: Persona Prompt

A cybersecurity programmer persona is defined to guide the AI models toward technical responses.

Step 4: OpenAI Integration

The program sends the prompt to:

OpenAI API Documentation

The response is extracted from the JSON output.

Step 5: Gemini Integration

The program interacts with:

Google Gemini API Documentation

The generated text is extracted from the API response.

Step 6: Hugging Face Integration

The program connects with:

Hugging Face Models

This demonstrates compatibility with open-source AI tools.

## Output Analysis

Feature	OpenAI	Gemini	Hugging Face
Accuracy	High	High	Moderate
Technical Depth	Excellent	Good	Basic
Clarity	Excellent	Good	Average
Response Length	Detailed	Moderate	Short
Code Quality	Strong	Good	Limited
Observations
OpenAI produced the most detailed technical explanation.
Gemini generated accurate but shorter responses.
Hugging Face generated simpler outputs due to the selected model.
Persona prompting improved technical depth in all models.
Structured prompts produced better results compared to vague prompts.
Advantages of Multi-AI Integration
Better response comparison
Increased reliability
Cross-validation of information
Automation of AI workflows
Improved decision-making
Applications

This approach can be used in:

Cybersecurity analysis
Reverse engineering research
Educational assistants
AI-powered coding tools
Automated report generation
Intelligent chatbot systems

## Conclusion

This experiment successfully demonstrated how Python can integrate with multiple AI tools using APIs. The program automated prompt submission, collected outputs, and compared response quality.

The Persona Pattern significantly improved technical responses, especially in cybersecurity-related tasks. Among the tested AI tools, OpenAI ChatGPT provided the most detailed and accurate response, while Google Gemini produced concise and structured explanations.

The experiment proves that combining multiple AI tools can improve reliability, analysis quality, and intelligent automation in real-world applications.

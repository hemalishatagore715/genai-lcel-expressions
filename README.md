## Design and Implementation of LangChain Expression Language (LCEL) Expressions

### AIM:
To design and implement a LangChain Expression Language (LCEL) expression that utilizes at least two prompt parameters and three key components (prompt, model, and output parser), and to evaluate its functionality by analyzing relevant examples of its application in real-world scenarios.

### PROBLEM STATEMENT:
To develop an LCEL-based application that generates structured content based on the user's input topic and required content length. The application should use a prompt template, a language model, and an output parser connected using the LCEL pipe operator (|).

### DESIGN STEPS:

#### STEP 1: Define the Prompt Template
- Import ChatPromptTemplate from LangChain.
- Create a prompt template with three input parameters:
    - email_content – Original email received.
    - tone – Required tone of the reply.
    - objective – Purpose of the reply.
- Provide instructions to generate a professional email response.

#### STEP 2: Initialize the Language Model
- Import FakeListChatModel from LangChain.
- Initialize the model with predefined email responses.
- Use predefined responses to simulate the email reply generation process without requiring an external API key.

#### STEP 3: Create the LCEL Chain and Generate Output
- Initialize StrOutputParser() to convert the model response into plain text.
- Connect the prompt, model, and output parser using the LCEL pipe (|) operator.
- Pass the original email, required tone, and reply objective using chain.invoke().
- Display the generated email reply.


### PROGRAM:

```python
```python
from langchain_core.prompts import ChatPromptTemplate
from langchain_core.output_parsers import StrOutputParser
from langchain_core.language_models.fake_chat_models import FakeListChatModel

prompt = ChatPromptTemplate.from_template("""
You are a professional email writing assistant.
Write a reply to the following email.
Original Email:
{email_content}
Required Tone:
{tone}
Reply Objective:
{objective}
Generate a clear, professional and relevant email reply.
""")

model = FakeListChatModel(
    responses=[
        "Dear Recruiter, Thank you for considering my application. I am interested in attending the interview. Tuesday or Thursday afternoon would work for me. Best regards.",
        "Dear Customer, We sincerely apologize for the inconvenience. Please share your order number and a photo of the damaged product so we can assist you.",
        "Dear Professor, I apologize for missing yesterday's class. Could you please let me know how I can catch up on the missed work? Thank you.",
        "Hi, I would be happy to reschedule our project meeting. Which alternative day would work best for you?",
        "Hello, I will share the project status update after completing the current review. Thank you for your patience.",
        "Thank you for your kind words. I really appreciate your support and help with the event."
    ]
)

parser = StrOutputParser()
chain = prompt | model | parser

response = chain.invoke({
    "email_content": "I would like to schedule an interview next week. Please share your availability.",
    "tone": "Professional and polite",
    "objective": "Thank the recruiter and express interest in attending the interview."
})

print("Generated Email Reply:")
print(response)
```

### OUTPUT:
<img width="1920" height="1080" alt="image" src="https://github.com/user-attachments/assets/6208beef-cdc9-4f82-ae4e-1cf39b836c55" />

### RESULT:
Thus, the LangChain Expression Language (LCEL) expression was successfully designed and implemented using three input parameters (email_content, tone, and objective) and three key components: Prompt, Model, and Output Parser. The components were connected using the LCEL pipe (|) operator to generate a professional email reply based on the given input.

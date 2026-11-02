## Design and Implementation of LangChain Expression Language (LCEL) Expressions

### AIM:
To design and implement a LangChain Expression Language (LCEL) expression that utilizes at least two prompt parameters and three key components (prompt, model, and output parser), and to evaluate its functionality by analyzing relevant examples of its application in real-world scenarios.

### PROBLEM STATEMENT:

### DESIGN STEPS:

#### STEP 1:

#### STEP 2:

#### STEP 3:

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
```

### OUTPUT:
<img width="1920" height="1080" alt="image" src="https://github.com/user-attachments/assets/6208beef-cdc9-4f82-ae4e-1cf39b836c55" />

### RESULT:

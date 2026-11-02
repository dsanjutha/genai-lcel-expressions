## Design and Implementation of LangChain Expression Language (LCEL) Expressions

### AIM:
To design and implement a LangChain Expression Language (LCEL) expression that utilizes at least two prompt parameters and three key components (prompt, model, and output parser), and to evaluate its functionality by analyzing relevant examples of its application in real-world scenarios.


### Problem statement:



To develop a LangChain Expression Language (LCEL) application that generates simple and customized explanations for different topics based on the target audience. The application uses two prompt parameters, topic and audience, and integrates a prompt template, OpenAI language model, and output parser to generate responses for real-world applications in education, business, and healthcar



### DESIGN STEPS:
Step 1: Import the required libraries, including LangChain, dotenv, and OpenAI.

Step 2: Load the OpenAI API key using load_dotenv().

Step 3: Create a prompt template using two parameters: {topic} and {audience}.

Step 4: Initialize the ChatOpenAI model and StrOutputParser to generate and format the response.

Step 5: Combine the three components using the LCEL pipe operator (|), execute different examples using chain.invoke(), and display the output.


### program:
```python
import os
from dotenv import load_dotenv
from langchain_core.prompts import ChatPromptTemplate
from langchain_openai import ChatOpenAI
from langchain_core.output_parsers import StrOutputParser

load_dotenv()

# Prompt
prompt = ChatPromptTemplate.from_template(
    "Explain {topic} for {audience} in 3 simple points."
)

# Model
model = ChatOpenAI(
    model="gpt-4o-mini",
    temperature=0.5
)

# Output Parser
parser = StrOutputParser()

# LCEL Chain
chain = prompt | model | parser

# Examples
for topic, audience in [
    ("Artificial Intelligence", "Students"),
    ("Chatbots", "Business Owners"),
    ("Machine Learning", "Healthcare Students")
]:
    result = chain.invoke({
        "topic": topic,
        "audience": audience
    })
    print(f"\n{topic}:\n{result}")
```





### OUTPUT:
<img width="1123" height="698" alt="image" src="https://github.com/user-attachments/assets/720187be-d8cb-49a3-bcc6-fa0d726fd527" />


### RESULT:
Thus, the LCEL application was successfully implemented using two prompt parameters (topic and audience) and three components (Prompt, Model, and Output Parser). It generated customized explanations for education, business, and healthcare applications.

# AI-real-estate-agent-using-langchain
Welcome to the AI Real Estate Agent project! This project leverages advanced AI models to provide personalized property recommendations based on buyer preferences. The AI real estate agent analyzes a list of properties and generates summaries highlighting how well each property matches the buyer's criteria.

Features
Personalized Property Summaries: Generate detailed summaries for each property based on buyer preferences.
Dynamic Property Listings: Easily update and manage property listings.
Advanced AI Integration: Utilize state-of-the-art language models to provide accurate and engaging property descriptions.
Getting Started
Prerequisites
Python 3.9 or higher
Install required packages:
pip install langchain openai pandas
Installation
Clone the repository:

git clone https://github.com//Poojakatta/AI-real-estate-agent-using-langchain.git
Set up your environment:

Ensure you have an OpenAI API key. You can get one here.
Create a .env file in the root directory and add your API key:
OPENAI_API_KEY=your_openai_api_key
Usage
Define the Prompt Template:

from langchain.prompts import PromptTemplate
from langchain.chains import LLMChain
from langchain.chat_models import ChatOpenAI

# Define the prompt template
prompt = """
You are an expert AI real estate agent. Based on the buyer's preferences, provide a personalized summary for each property.

Buyer's Preferences:

Neighborhood: {Neighborhood}
Price: {Price}
Bedrooms: {Bedrooms}
Bathrooms: {Bathrooms}
House Size: {House_Size}

List of Properties:
{properties}

Task: Based on the buyer's preferences, provide a personalized summary for each property, highlighting how well it matches their criteria and any unique features that may appeal to them. Do not change the original details of the property. If you didn't find any property matching their preferences, suggest something similar. If something similar is also not found, say you didn't find any properties as per their requirement.
"""

# Define the input variables
input_variables = ["Neighborhood", "Price", "Bedrooms", "Bathrooms", "House_Size", "properties"]

# Create the PromptTemplate object
prompt_template = PromptTemplate(
    input_variables=input_variables,
    template=prompt
)
Initialize the Language Model:

llm = ChatOpenAI(model="gpt-3.5-turbo", temperature=1, max_tokens=4000)
Create the LLMChain:

chain = LLMChain(llm=llm, prompt=prompt_template)
Generate Property Listings:

buyer_preferences = {
    "Neighborhood": "Lakefront",
    "Price": "$1,000,000 - $1,500,000",
    "Bedrooms": "4",
    "Bathrooms": "3",
    "House_Size": "3,000 - 4,000 sqft",
    "properties": """
    1. Property 1: Neighborhood: Lakefront Paradise, Price: $1,200,000, Bedrooms: 4, Bathrooms: 3, House Size: 3,500 sqft
    2. Property 2: Neighborhood: Mountain Retreat, Price: $900,000, Bedrooms: 4, Bathrooms: 3, House Size: 2,800 sqft
    """
}

response = chain.run(buyer_preferences)
print(response)
Contributing
We welcome contributions! Please read our contributing guidelines for details on how to get started.

License
This project is licensed under the MIT License. See the LICENSE file for details.

Acknowledgments
LangChain for providing the framework for prompt templates and LLM chains.
OpenAI for the powerful language models.

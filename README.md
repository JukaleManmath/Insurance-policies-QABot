
# Insurance Guidelines QABot

This is a Streamlit web application for the Insurance Guidelines QABot, which uses the Lyzr library for natural language processing (NLP) and OpenAI's GPT-3.5-turbo model to answer questions related to insurance guidelines from uploaded PDF documents.

# Requirements

- Python 3.x
- Streamlit
- Lyzr
- WeaviateVectorStore
- An OpenAI API Key

# Installation

1. Clone the repository:

   ```bash
   git clone https://github.com/your-repo/insurance-guidelines-qabot.git
   cd insurance-guidelines-qabot
   ```

2. Install the required packages from the requirements

3. Set up the OpenAI API key:

   Before running the app, set your OpenAI API key in the code:
   
   ```python
   os.environ['OPENAI_API_KEY'] = 'sk-YourAPIKeyHere'
   ```

#Usage

To run the application, use the following command:

```bash
streamlit run app.py
```

This will start the Streamlit server and open the app in your default web browser.

# How to Use

1. Upload Insurance Guidelines PDF:
   - Use the file uploader in the sidebar to upload an insurance guideline PDF.

2. Ask Questions:
   - Once the PDF is uploaded, you can ask your questions about insurance guidelines in the provided text input field.

3. Get Answers:
   - Click the "Get Answer" button to trigger the QABot to process your question.
   - The QABot will display the most relevant answer extracted from the uploaded PDF.

4. Source Nodes:
   - If applicable, the QABot will also display "Source Nodes" which show the specific sections or sources within the PDF related to the answer.

## Customization

### Styling
The app includes custom styling for a better user experience. You can modify the styles in the `main()` function:

```python
st.set_page_config(
    page_title="Insurance Guideline QABot",
    page_icon=":shield:",
    layout="wide",
    initial_sidebar_state="expanded"
)

st.markdown(
    """
    <style>
    body {
        background-color: #87CEEB; 
        color: #FFFFFF;
    }
    .stApp {
        background-color: rgba(0, 0, 0, 0.8); 
        color: #FFFFFF; 
    }
    .stTextInput > div > div > input {
        color: #FFFFFF; 
    }
    .stButton {
        background-color: #4CAF50; 
        color: #FFFFFF; 
    }
    .stButton:hover {
        background-color: #45a049; 
    }
    .stMarkdown {
        color: #FFFFFF; 
    }
    </style>
    """,
    unsafe_allow_html=True
)
```

# QABot Initialization
You can customize the QABot's initialization by modifying the `initialize_qa_bot()` function:

```python
def initialize_qa_bot(pdf_file_path):
    vector_store_params = {
        "vector_store_type": "WeaviateVectorStore",
        "index_name": "IndexName"  
    }
    qa_bot = QABot.pdf_qa(
        input_files=[pdf_file_path],
        vector_store_params=vector_store_params,
    )
    return qa_bot
```

# Benefits

- Simplifies Insurance Understanding: Users can quickly get answers to insurance-related questions without the need to manually search through lengthy documents.
  
- Time-Saving: Saves valuable time for both insurance professionals and policyholders by providing instant answers.
  
- Enhanced Accuracy: Utilizes advanced NLP capabilities to extract accurate information from insurance guidelines.
  
- Improved Accessibility: Bridges the gap between complex insurance policies and everyday users with a user-friendly interface.
  
- Source Verification: Displays "Source Nodes" for transparency, allowing users to verify information within the PDF.
  
- Continuous Learning: Acts as a virtual assistant, guiding users through queries and providing educational insights.

# Acknowledgements

- Streamlit: https://streamlit.io/
- Lyzr: https://lyzr.io/
- OpenAI: https://openai.com/


TaxMate: RAG-based Tax Law Query Bot
TaxMate is a Retrieval-Augmented Generation (RAG)-based chatbot designed to provide accurate and contextual answers to Indian tax law queries. It aims to simplify complex tax provisions for the general public by grounding responses in official legal documents, minimizing hallucinations, and ensuring factual accuracy.

This project was developed as part of the B.Tech in Computer Science and Engineering (AI) program at Mar Baselios College of Engineering & Technology, affiliated with APJ Abdul Kalam Technological University.

✨ Features
Retrieval-Augmented Generation (RAG) Pipeline: Implements a comprehensive RAG pipeline including embedding, retrieval, reranking, and generation stages.

Efficient Semantic Retrieval: Utilizes SBERT (Sentence-BERT) for generating embeddings and FAISS for fast semantic search.

Enhanced Relevance: Integrates the Cohere Rerank API to improve the relevance of retrieved documents.

Local LLM Integration: Employs a locally hosted LLaMA 2-7B model (4-bit quantized) for generating user-friendly responses.

User-Friendly Interface: Provides a real-time, interactive chat experience through a Streamlit frontend.

Domain-Specific Responses: Generates legally grounded and contextually relevant answers, significantly reducing factual errors and hallucinations.

Resource-Efficient: Designed to run efficiently on consumer-grade GPUs, making it accessible for wider use.

🏗️ System Architecture
TaxMate's architecture is structured to ensure robust and accurate information retrieval and generation:

Data Preparation: Indian Income Tax law PDFs are processed and converted into a structured JSON format.

Embeddings Generation: Text chunks from the prepared data are converted into numerical embeddings using the all-MiniLM-L6-v2 model (SBERT).

Retrieval: A FAISS index is built from these embeddings, enabling fast and efficient semantic search to identify relevant document chunks.

Reranking: The top retrieved results are further refined using the Cohere Rerank API to prioritize the most relevant passages.

Generation: The reranked content is fed as context to a LLaMA 2-7B model (instruction-tuned, 4-bit quantized), which then generates the final, grounded answer.

Frontend: A Streamlit application serves as the interactive chatbot interface, allowing users to submit queries and receive responses.

📊 Evaluation
The performance of TaxMate's responses was rigorously evaluated using a combination of reference-based and reference-less metrics:

Reference-Based Metrics: BLEU, METEOR, ROUGE, and BERTScore were used to compare generated responses against human-written reference answers.

Reference-Less Evaluation: QuESTEval was employed to assess response quality without the need for reference texts.

Comparative Analysis: Extensive comparisons were conducted against other large language models like Mistral AI and LLaMA 2. LLaMA 2 was ultimately selected for the final implementation due to its superior semantic alignment and ability to produce more user-friendly responses.

🚀 How to Run Locally
Follow these steps to set up and run TaxMate on your local machine:

1️⃣ Clone the Repository
git clone https://github.com/yourusername/taxmate-rag-query-bot.git
cd taxmate-rag-query-bot

2️⃣ Install Dependencies
It is highly recommended to create a virtual environment to manage dependencies:

python -m venv venv
# On Linux/macOS
source venv/bin/activate
# On Windows
venv\Scripts\activate

pip install -r requirements.txt

3️⃣ Prepare the Environment
Tax Law Data: Place your structured JSON tax law file (containing the processed PDF data) into the data/ directory.

FAISS Index & Embeddings: Ensure your FAISS index and corresponding embeddings are pre-generated. If not, run the embedding generation script provided in the project (e.g., python scripts/generate_embeddings.py).

Cohere API Key: Set your Cohere API Key as an environment variable. Replace "your_api_key" with your actual key.

export COHERE_API_KEY="your_api_key" # For Linux/macOS
# For Windows (Command Prompt)
set COHERE_API_KEY="your_api_key"
# For Windows (PowerShell)
$env:COHERE_API_KEY="your_api_key"

LLaMA 2 Weights: Download the LLaMA 2 model weights locally and update the LLAMA_PATH variable in the relevant code file (e.g., config.py or app.py) to point to the correct path of your downloaded model.

4️⃣ Run the Streamlit App
Once all dependencies are installed and the environment is prepared, you can launch the chatbot:

streamlit run app.py

This will open the TaxMate chatbot in your web browser.

🛠️ Tech Stack
Programming Language: Python

Vector Database: FAISS (for fast semantic retrieval)

Embedding Model: SBERT (SentenceTransformers)

NLP Framework: Hugging Face Transformers

Reranking API: Cohere Rerank API

Frontend Framework: Streamlit

Large Language Model: LLaMA 2-7B (4-bit Quantized)

🌍 Sustainable Development Goals (SDGs) Alignment
This project contributes to several United Nations Sustainable Development Goals:

SDG 16: Peace, Justice and Strong Institutions: By providing transparent and accessible information on legal and tax provisions, TaxMate promotes greater understanding and adherence to the rule of law.

SDG 10: Reduced Inequalities: Simplifying complex legal language makes essential information accessible to a wider audience, helping to reduce knowledge disparities.

SDG 9: Industry, Innovation and Infrastructure: Developing a resource-efficient AI solution for public services demonstrates innovation in leveraging technology for societal benefit.

📈 Future Scope
We envision the following enhancements for TaxMate:

Domain Expansion: Extend the bot's knowledge base to include other legal domains such as Goods and Services Tax (GST), labor laws, and corporate law.

Accessibility Features: Integrate speech-to-text and text-to-speech capabilities to enhance accessibility for diverse users.

Deployment & User Management: Develop and deploy TaxMate as a full-fledged web or mobile application, incorporating user sessions and query history.

Real-time Data Integration: Implement real-time updates by integrating with official APIs from the Income Tax Department.

Specialized LLMs: Explore the use of domain-specialized Large Language Models fine-tuned specifically on Indian legal texts for even greater accuracy and nuance.

🤝 Team
Akash A (B22CS2112)

Akash PR (B22CS2113)

Jyothsna P Nair (B22CS2137)

Sruthin LJ (B22CS2157)

📄 License
This project is intended for academic and educational purposes only. For collaboration opportunities or institutional adaptation of this system, please contact the project team members.

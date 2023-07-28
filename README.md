# QA with LLM and RAG (Retrieval Augmented Generation)

This project is an Question Answering application with Large Language Models (LLMs) and Amazon Aurora Postgresql. An application using the RAG(Retrieval Augmented Generation) approach retrieves information most relevant to the user’s request from the enterprise knowledge base or content, bundles it as context along with the user’s request as a prompt, and then sends it to the LLM to get a GenAI response.

LLMs have limitations around the maximum word count for the input prompt, therefore choosing the right passages among thousands or millions of documents in the enterprise, has a direct impact on the LLM’s accuracy.

In this project, Amazon Aurora Postgresql with pgvector is used for knowledge base.

The overall architecture is like this:

![rag_with_pgvector_arch](./cdk_stacks/rag_with_pgvector_arch.svg)

### Overall Workflow

1. Deploy the cdk stacks (For more information, see [here](./cdk_stacks/README.md)).
  - A SageMaker Endpoint for text generation.
  - A SageMaker Endpoint for generating embeddings.
  - An Amazon Aurora Postgresql cluster for storing embeddings.
  - Aurora Postgresql cluster's access credentials (username and password) stored in AWS Secrets Mananger as a name such as `RAGPgVectorStackAuroraPostg-xxxxxxxxxxxx`.
2. Open SageMaker Studio and then open a new **System terminal**.
3. Run the following commands on the terminal to clone the code repository for this project:
   ```
   git clone https://github.com/ksmin23/rag-with-postgres-pgvector.git
   ```
4. Open `data_ingestion_to_pgvector` notebook and Run it. (For more information, see [here](./data_ingestion_to_vectordb/data_ingestion_to_pgvector.ipynb))
5. Run Streamlit application. (For more information, see [here](./app/README.md))

### References

  * [Leverage pgvector and Amazon Aurora PostgreSQL for Natural Language Processing, Chatbots and Sentiment Analysis](https://aws.amazon.com/blogs/database/leverage-pgvector-and-amazon-aurora-postgresql-for-natural-language-processing-chatbots-and-sentiment-analysis/)
  * [Building AI-powered search in PostgreSQL using Amazon SageMaker and pgvector](https://aws.amazon.com/blogs/database/building-ai-powered-search-in-postgresql-using-amazon-sagemaker-and-pgvector/)
  * [Build Streamlit apps in Amazon SageMaker Studio](https://aws.amazon.com/blogs/machine-learning/build-streamlit-apps-in-amazon-sagemaker-studio/)
  * [Quickly build high-accuracy Generative AI applications on enterprise data using Amazon Kendra, LangChain, and large language models](https://aws.amazon.com/blogs/machine-learning/quickly-build-high-accuracy-generative-ai-applications-on-enterprise-data-using-amazon-kendra-langchain-and-large-language-models/)
  * [Question answering using Retrieval Augmented Generation with foundation models in Amazon SageMaker JumpStart](https://aws.amazon.com/blogs/machine-learning/question-answering-using-retrieval-augmented-generation-with-foundation-models-in-amazon-sagemaker-jumpstart/)
  * [LangChain](https://python.langchain.com/docs/get_started/introduction.html) - A framework for developing applications powered by language models.
  * [Streamlit](https://streamlit.io/) - A faster way to build and share data apps

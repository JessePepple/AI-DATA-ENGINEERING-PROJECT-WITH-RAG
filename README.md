# AI-Data-Engineering-Project-With-RAG


This is an AI Data Engineering project focused on building a Retrieval-Augmented Generation (RAG) pipeline using LangChain and ChromaDB. I started by converting raw text into documents, followed by splitting the documents into smaller chunks for efficient processing. I then generated embeddings for each chunk and stored both the chunks and their corresponding embeddings in a ChromaDB vector database. Finally, I performed semantic search against the vector database to retrieve the most relevant information based on user queries.


### Phase 1 RAG Application with Text:

As the first stage of the project, I started with a text input and converted it into a LangChain `Document` object using `from langchain_core.documents import Document`. Converting the raw text into a structured document makes it easier to manage the data and prepare it for the next stage of the RAG pipeline, where the document is split into smaller chunks for embedding and retrieval.


<img width="1146" height="566" alt="image" src="https://github.com/user-attachments/assets/b6e3a8ae-135b-4fea-b22f-e87a22a2a7ae" />

After creating the LangChain `Document`, I followed the standard RAG chunking process by splitting the document into smaller, manageable chunks. This allows large pieces of text to be processed more efficiently and improves the accuracy of retrieval by enabling the system to identify and retrieve specific sections of relevant information rather than processing the entire document at once.


<img width="1146" height="566" alt="Screenshot 2026-10-07 at 17 34 07" src="https://github.com/user-attachments/assets/dd8f03a2-13a9-447d-8b8c-2f42f1912a82" />

Once the document had been split into chunks, the next stage was to generate embeddings for each chunk. The embedding model converts the text into numerical vector representations that capture the semantic meaning of the content. I then stored both the generated embeddings and their corresponding text chunks in ChromaDB, which acts as the vector database for the RAG pipeline. This allows the system to efficiently perform similarity searches and retrieve the most relevant chunks when a user submits a query.


<img width="1146" height="566" alt="Screenshot 2026-10-07 at 17 39 03" src="https://github.com/user-attachments/assets/9f37287f-2682-482c-aaac-b48645e13df6" />


Finally, to validate the RAG workflow, I queried the application using questions based on the context of the documents I provided. The application performed a semantic search against ChromaDB to identify and retrieve the most relevant chunks of information. This allowed me to verify that the embeddings, vector storage, and retrieval process were working correctly and that the application could return contextually relevant information from the original documents.

<img width="1146" height="566" alt="Screenshot 2026-10-07 at 17 41 45" src="https://github.com/user-attachments/assets/e645d4cb-a14a-4de0-89e8-3ac73c3c36d3" />
<img width="1146" height="566" alt="Screenshot 2026-10-07 at 17 41 52" src="https://github.com/user-attachments/assets/80f0d6e1-5d3a-40e9-b59f-8e068cc74808" />


### RAG Application With Documents:
After validating the initial RAG workflow using raw text, I moved on to working with a real-world document. For this stage, I used a PDF containing an overview of Microsoft OneLake. The goal was to demonstrate how the RAG pipeline could ingest and process a structured document rather than relying solely on manually provided text. The PDF was loaded into the pipeline and prepared for the same chunking, embedding, vector storage, and semantic retrieval workflow used in the previous stage.

<img width="1146" height="566" alt="Screenshot 2026-10-07 at 17 45 09" src="https://github.com/user-attachments/assets/b71643ec-5bb9-46c0-8371-fe64cb31e876" />


The workflow remained largely the same as the previous text-based implementation, with minimal changes required. The main difference was extracting the PDF document from a specified file path before passing its contents through the existing RAG pipeline. Once extracted, the document followed the same process of chunking, embedding generation, storage in ChromaDB, and semantic search.


<img width="1146" height="566" alt="Screenshot 2026-10-07 at 17 46 24" src="https://github.com/user-attachments/assets/2ad593a5-d6ef-4c26-89c8-9acff945597a" />

#### Chunking

<img width="1146" height="566" alt="Screenshot 2026-10-07 at 17 48 44" src="https://github.com/user-attachments/assets/0e278e15-68d8-446d-87d5-b45f2c5cc84e" />



#### Embedding & Loading to Vector Store

<img width="1146" height="566" alt="Screenshot 2026-10-07 at 17 49 16" src="https://github.com/user-attachments/assets/f46d72b1-e870-4d04-982a-d077acaf9613" />

#### Semantic Search & Talking To LLM

<img width="1146" height="566" alt="Screenshot 2026-10-07 at 17 49 55" src="https://github.com/user-attachments/assets/232d8929-d8c8-47c4-9d58-3f8f248c62b7" />

<img width="1146" height="566" alt="Screenshot 2026-10-07 at 17 50 19" src="https://github.com/user-attachments/assets/a2a8e3b9-05af-40e3-9758-402bb35e965c" />


### Local Persists & Adding Another Documents

Instead of storing the vector data in ChromaDB's default storage location, I configured the project to persist the vector data locally in a folder named `Vector`. I then added a new document to the vector store, allowing the RAG application to retrieve additional context from the newly ingested information. Finally, I used Docker Model Runner to support local model execution and make it easier to rerun and test the RAG workflow consistently.


<img width="1146" height="566" alt="Screenshot 2026-10-07 at 17 57 38" src="https://github.com/user-attachments/assets/06758635-3f10-4e85-ba04-90f3fe62c1a1" />
<img width="1146" height="566" alt="Screenshot 2026-10-07 at 17 58 04" src="https://github.com/user-attachments/assets/7cb042a4-ece9-440f-a636-b940e186d6fc" />
<img width="1146" height="566" alt="Screenshot 2026-10-07 at 17 58 04" src="https://github.com/user-attachments/assets/7cb042a4-ece9-440f-a636-b940e186d6fc" />
PDF → Extract Document → Chunking → Embeddings → Local Vector Storage → Add New Documents → RAG Context Retrieval → Docker Model Runner

### Conclusion

Overall, this project provided a practical implementation of a Retrieval-Augmented Generation (RAG) workflow, demonstrating how unstructured data can be transformed into useful context for an AI application. I progressed from working with raw text to processing real-world PDF documents, converting content into LangChain documents, chunking the data, generating embeddings, and storing the resulting vectors for semantic retrieval. I also explored local vector persistence using ChromaDB and a dedicated `Vector` folder, allowing additional documents to be incorporated into the application. Finally, I used Docker Model Runner to support local model execution and rerunning of the workflow. This project helped demonstrate the end-to-end process of preparing data for RAG applications while strengthening my understanding of document processing, embeddings, vector and semantic search.



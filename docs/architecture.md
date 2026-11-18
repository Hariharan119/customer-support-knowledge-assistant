# Architecture

## Diagram
```
   SUPPORT AGENT
      | asks a product question
      v
   STREAMLIT FRONTEND
      | sends question to backend
      v
   FASTAPI BACKEND
      | searches for relevant passages
      v
   RETRIEVAL LAYER <---- SUPPORT DOCUMENTS (manuals, FAQs)
      |                         |
      |                         +--> text extraction / chunking
      |                         +--> embeddings
      |                         +--> FAISS or Pinecone index
      |
      | question + retrieved context
      v
   LLM API
      | grounded response
      v
   FASTAPI BACKEND
      |
      v
   STREAMLIT FRONTEND
      |
      v
   AGENT SEES ANSWER + SOURCE / SAFE FALLBACK
```

## Component roles
| Component         | Responsibility      | Simple explanation                                                           |
|:------------------|:--------------------|:-----------------------------------------------------------------------------|
| Streamlit         | Frontend            | The screen through which the user interacts.                                 |
| FastAPI           | Backend/API         | Receives requests, validates input and coordinates services.                 |
| LLM API           | Language generation | Creates a natural-language response using the question and supplied context. |
| Embeddings        | Text representation | Converts text into numerical vectors for similarity-based retrieval.         |
| FAISS / Pinecone  | Vector search       | Helps find passages semantically relevant to the question.                   |
| Support documents | Knowledge source    | Provide information the assistant is allowed to use.                         |

## Request and response flow
1. An agent enters: "How long is the warranty on this product?"
2. Streamlit sends the question to a FastAPI endpoint.
3. FastAPI passes the question to the retrieval component.
4. The retrieval component searches the indexed support passages.
5. Relevant passages are supplied to the LLM with instructions to answer only from the supplied context.
6. The backend returns the answer and available source information to Streamlit.
7. If no useful passage is found, the application displays a safe message instead of inventing an answer.

## Technology stack
| Layer            | Selected technology                       | Reason                                                                                 | Account / access requirement                                    | Fallback option           |
|:-----------------|:------------------------------------------|:---------------------------------------------------------------------------------------|:----------------------------------------------------------------|:--------------------------|
| Frontend         | Streamlit                                 | Quickly build a Python-based interface.                                                | None                                                            | -                         |
| Backend          | FastAPI                                   | Expose application functionality through APIs; implementation on Day 32.               | None                                                            | -                         |
| LLM integration  | OpenAI API                                | Generate language responses.                                                           | Approved API credentials, secure key handling, usage monitoring | Another approved LLM API  |
| Embeddings       | Compatible embedding model/API            | Represent text for semantic retrieval.                                                 | Same API access as the LLM                                      | Alternate embedding model |
| Vector store     | FAISS                                     | Simple local vector search for the prototype; data size and persistence to be checked. | None                                                            | Pinecone                  |
| Version control  | GitHub                                    | Collaborate and track code changes.                                                    | GitHub account and repository access                            | -                         |
| Containerization | Docker                                    | Package the application after implementation (Day 34).                                 | Docker installed                                                | Run locally               |
| Cloud            | Azure                                     | Deploy the application, subject to access.                                             | Subscription, permissions, approved region                      | Run locally               |
| CI/CD            | GitHub Actions or approved Azure pipeline | Automate build and deployment steps (Day 34).                                          | Repository permissions                                          | Manual deployment         |
| Testing          | Pytest                                    | Create repeatable tests.                                                               | None                                                            | -                         |

# Problem Statement

## User
Customer support agents and new support team members.

## Business problem
Agents search through product manuals and FAQ documents to answer the same customer questions again and again.

## Proposed solution
A question-answering assistant that retrieves relevant information from approved support documents and uses an LLM to produce a concise response.

## Statement
Customer support agents find it difficult to locate accurate answers across many product manuals and FAQ documents. We will develop an AI-powered knowledge assistant that allows agents to ask questions in natural language and receive concise answers grounded in approved support documents.

## Scope
| Decision         | Customer Support Knowledge Assistant                                                                  |
|:-----------------|:------------------------------------------------------------------------------------------------------|
| Project type     | Chatbot / document-grounded Q&A assistant                                                             |
| Input            | Agent's natural-language question                                                                     |
| Processing steps | Retrieve relevant passages, send them with the question to the LLM, return the answer with its source |
| Knowledge source | Synthetic or approved sample manuals and FAQs                                                         |
| Output           | Answer based on retrieved text; indicate when information is not found                                |
| MVP feature 1    | Question input and answer display                                                                     |
| MVP feature 2    | Retrieve relevant passages from support documents                                                     |
| MVP feature 3    | Generate a concise answer using an LLM                                                                |
| MVP feature 4    | Show source document or section when available                                                        |
| MVP feature 5    | Show a safe fallback when documents do not support an answer                                          |
| Postponed        | Agent login integration, ticket creation, refund or order actions, write access to company systems    |

## Success criteria
- A product question returns a correct short answer with its source.
- A question not covered by the documents returns the safe fallback message.

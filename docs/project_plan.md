# Project Plan

## Milestones
|   Day | Milestone                                                                              |
|------:|:---------------------------------------------------------------------------------------|
|    31 | Project setup and architecture                                                         |
|    32 | FastAPI backend setup, LLM API integration, embeddings and retrieval, endpoint testing |
|    34 | Docker, Azure deployment, CI/CD                                                        |

## Team roles
| Member    | Role                       | Day 31 responsibility                             | Later contribution          |
|:----------|:---------------------------|:--------------------------------------------------|:----------------------------|
| Hariharan | Architecture & Integration | Own blueprint and repository structure            | Coordinate integration      |
| Member 2  | Backend                    | List API requirements and request/response fields | Build FastAPI endpoints     |
| Member 3  | AI/LLM                     | Define prompt, context and retrieval flow         | Implement LLM and retrieval |
| Member 4  | Frontend                   | Sketch user journey and screens                   | Build Streamlit interface   |
| Member 5  | DevOps & QA                | Check access and prepare test/deployment plan     | Docker, Azure and testing   |

## Risks
| Risk                             | Mitigation                                  |
|:---------------------------------|:--------------------------------------------|
| API access not available         | Validate access early                       |
| Inaccurate or invented answers   | Source-grounded prompts                     |
| Missing information in documents | Safe fallback message                       |
| Cloud permissions                | Check permissions early and record blockers |

## Dependencies
Backend endpoints, LLM credentials, sample documents and the retrieval approach for Day 32.

## Azure readiness
| Check        | Status                                                                                           |
|:-------------|:-------------------------------------------------------------------------------------------------|
| Subscription | Approved training subscription, to be confirmed by team                                          |
| Permissions  | Check resource creation and deployment permissions                                               |
| Region       | Use the region approved for the training environment                                             |
| Resources    | Hosting option and supporting services to be finalized after architecture review                 |
| Secrets      | Use approved secret storage; never hard-code API keys                                            |
| Cost control | Create only approved resources; stop or delete temporary resources according to lab instructions |
| Blockers     | Record missing roles, quota, policy or access issues and the administrator who can resolve them  |

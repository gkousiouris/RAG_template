# RAG_template
This is a repo to hold a template structure for a RAG stack including all necessary dependencies.

# Responsible AI Use Disclaimer
In this section I describe the process that led to the development of the template RAG structure with the use of AI, including process details for future reference.<br />

The initial compose file was generated with the help of ChatGPT 5.0 with the following prompts:<br />
`I want a docker compose file that will setup a local genai stack for rag`
Following I queried about key requirements that I wanted to clarify based on the intended use of the RAG pipeline:
`Is this solution multitenant?can it support different user sessions?`
The reply was that it supports multitenancy at the user end, but with a common embeddings and documents backend, which was my requirement. If one needs separate vector data per tenant/user, then there are some configuration modifications that need to be made. This was not my use case.

Following, approximately 7-8 hours were needed in order to debug the initially provided compose file and finalize it into a working version, since a number of bugs were discovered in the initial ChatGPT output. One of the main confusing ones was the use of curl to check out the health of the dependent containers, while the curl tool was not included in the main images of the compose file.

Based on the initial tests, further modifications were performed, in order to change the base embeddings model used (bge-base-en-v1.5) from the initial small suggestion, as well to some options available in OpenWebUI.
SCREENSHOT OF OPTIONS

New document inclusion is supported via the Open Web UI uploading. At the moment the process relies on llama3.2:3b, which is hardcoded as an option in the compose file. The model is retrieved unless it is already available locally. 

The above compose template has been tested in Docker Desktop for Windows 11. If you have any suggestions for improvements I will be happy to consider them.

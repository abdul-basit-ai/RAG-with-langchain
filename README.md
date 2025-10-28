# RAG on documentation using LANGCHAIN 
### Pdf contains the detailed notes
In this project, I build a RAG based system for answering questions on hugging face documentation using hugging face model "HuggingFaceH4/zephyr-7b-beta" which is small but powerful model. I also used LangChian as it offers variety of options for vectore database.
I first splitted the documents from my dataset into smaller chunks which will be a knowledge base for our model. The goal is to prepare a collection of semantically relevant snippets. I used recursive chunking here to get the chunks from data where first it will break from double line the single line, followed by where sentence end then finally where it fits our chunk size length. Then these chunks are embedded using embedding model "thenlper/gte-small".

Then I build the vector space, where I stored the embedding of the chunks and remeber the user query will also be embedded by same embedded model used previously. Then we will run search algorithm to find the relevant chunks based on user query. There are plentiful choices for the nearest neighbor search algorithm: we go with Facebook’s FAISS since FAISS is performant enough for most use cases, and it is well known and thus widely implemented. And the distance measuring I used cosine similarity.

NOTE: But the best I have seen used by Qdrant is (Hierarchical navigable small world-HNSW) definately check it out. 

Then Finally these chunks embedding together with user query are fed into llm to generate specific answer.
<img width="607" height="854" alt="image" src="https://github.com/user-attachments/assets/4e63f51a-0825-463d-bd20-f0c12c46fcbe" />

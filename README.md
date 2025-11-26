# image-search
CLIP + FAISS


# Frontend
- Using transformers.js, the frontend runs a CLIP model to generate an embedding vector for the input image.
- The embedding is then http POST to the backend for similarity search.


# Backend
The backend uses a FAISS index built from embeddings of all images stored in the database.
When an image-search request arrives from the frontend, the backend:
1. Takes the submitted embedding.
2. Searches the FAISS index for the nearest matches.
3. Uses the returned FAISS indices to look up the corresponding image metadata in an array.
  - The metadata array is aligned with the FAISS index, so each FAISS vector index matches the same position in the metadata array.
This retrieves the most similar images efficiently and accurately.

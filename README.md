# Final-Project-Ironhack
Repository to Ironhack DS&amp;ML bootcamp final project.

Experiências a Dois — RAG Chatbot with Affiliate Recommendations

This project implements a Retrieval-Augmented Generation (RAG) chatbot for the blog experienciasadois.com

It combines semantic search over blog articles with OpenAI generative models, and enriches responses with affiliate links (hotels, activities, experiences).


FEATURES:
RAG pipeline: query → retrieve top blog passages (Chroma + embeddings) → generate answer (OpenAI).

Multilingual support: We support queries in both Portuguese and English.

Affiliate blocks: injects relevant affiliate offers (hotels, activities) based on destination detection.

Flask API with endpoints /chat/retrieve and /chat/answer.

CORS is enabled to connect with the WordPress frontend widget.

Ready for deployment to AWS (Elastic Beanstalk or App Runner).

ea2-flask-api/
├─ application.py        # Flask app (API endpoints)
├─ runtime_rag.py        # RAG pipeline functions + state initialization
├─ requirements.txt      # Python dependencies
├─ runtime.txt           # (optional, for AWS Elastic Beanstalk)
├─ data/
│   └─ aff.csv           # Affiliate links (page_name, experience_name, affiliate_url, destination, type…)
└─ chroma_blog/          # Persisted ChromaDB index (or downloaded from S3 at runtime)


WordPress Integration

Use a Custom HTML block in WordPress to embed the frontend widget.
Update API_BASE in the JS snippet to point to your API (Elastic Beanstalk or App Runner URL).


Notes:

Keep ChromaDB version consistent between indexing and runtime (0.5.x vs 1.0.x).

Restrict CORS origins in production for security.

The Affiliate CSV can be stored locally in the data/directory or loaded from S3 at runtime.

To update affiliate offers, just replace the CSV and restart the service.



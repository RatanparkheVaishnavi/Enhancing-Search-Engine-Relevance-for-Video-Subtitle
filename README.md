# **Video Subtitle Search Engine (Shazam for Subtitles)**  

## **Overview**  
This project enhances **video subtitle search relevance** by leveraging **Natural Language Processing (NLP)** and **Machine Learning (ML)**. It enables users to search subtitles using both **keyword-based** and **semantic search** techniques.  

## **Features**  
✅ Extracts subtitles from a **SQLite database**  
✅ Preprocesses text (removing timestamps, cleaning)  
✅ Supports **Keyword-Based Search** (TF-IDF + Cosine Similarity)  
✅ Supports **Semantic Search** (BERT embeddings with ChromaDB)  
✅ **Document Chunking** to preserve context  
✅ **Optimized for Google Colab**  

## **Tech Stack**  
- **Python**   
- **SQLite3** for database handling  
- **Pandas** & **NumPy** for data processing  
- **Scikit-learn** for TF-IDF & similarity calculations  
- **Sentence Transformers** for BERT-based embeddings  
- **ChromaDB** for storing and retrieving semantic embeddings  

## **Installation & Setup**  

### **1. Install Dependencies**  
Run the following in **Google Colab**:  
```bash
!pip install chromadb sentence-transformers
```

### **2. Load the Database**  
- **Upload** `eng_subtitles_database.db` to **Google Drive**  
- **Mount Google Drive** in Colab:  
```python
from google.colab import drive
drive.mount('/content/drive')
```
- Set the database path:  
```python
db_path = "/content/drive/MyDrive/eng_subtitles_database.db"
```

### **3. Run the Script**  
```python
query = "A detective investigating a crime"
print("🔍 Semantic Search Results:", search_subtitles(query, method='semantic'))
print("🔍 Keyword Search Results:", search_subtitles(query, method='keyword'))
```

## **How It Works**  
1. **Reads subtitles from the database**  
2. **Cleans text** (removes timestamps & unwanted characters)  
3. **Generates embeddings** using **TF-IDF & BERT**  
4. **Stores embeddings** in **ChromaDB**  
5. **Retrieves relevant results** based on user queries  

## **Example Query Output**  
```
🔍 Semantic Search Results:
[
  {"name": "crime_movie.srt", "content": "The detective investigates the case..."},
  {"name": "thriller_series.srt", "content": "A thrilling crime unfolds..."}
]
```

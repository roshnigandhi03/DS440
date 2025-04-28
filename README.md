# AI Recipe Generator Model using Retrieval-Augmented Generation (RAG)

## Overview
This project implements an AI-powered Recipe Generator that produces customized recipes based on user-input ingredients. It leverages Retrieval-Augmented Generation (RAG) for enhanced contextual relevance, using:
* **LangChain** for orchestration
* **FAISS** (Facebook AI Similarity Search) for efficient vector storage and retrieval
* **Gemma-3-1b-it** (a lightweight instruction-tuned model) for text generation.
Users input a list of available ingredients, and the system generates tailored recipes using both a semantic database of recipes and the generation capabilities of the language model.

## Features
* Ingredient-based recipe generation
* RAG pipeline combining retrieval and generation
* Preprocessing and vector embedding of a large recipe dataset
* Semantic search with FAISS for fast retrieval
* Custom text generation using Google's Gemma-3-1b-it model
* Deployable in a lightweight environment like Google Colab

## Architecture
### Data Preparation
* A large .csv dataset of recipes is loaded and preprocessed
* Text data is split into chunks using LangChain’s ```CharacterTextSplitter```.
### Embedding and Indexing
* Embeddings are generated using **HuggingFace sentence-transformers**.
* **FAISS** is used to index the recipe embeddings for efficient retrieval.
### RAG Pipeline
* For a given query (list of ingredients), relevant chunks are retrieved from FAISS.
* Retrieved context is fed to the Gemma-3-1b-it model using a prompt template.
* LangChain's RetrievalQA chain structure is used to manage retrieval and answer generation.
### User Interaction
* A simple function interface for users to input ingredients in a comma-separated format and get a generated recipe.

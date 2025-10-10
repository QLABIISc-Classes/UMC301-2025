# LangChain Exercises

This repository contains exercises adapted from the educational content by [Coding Crashkurse](https://github.com/Coding-Crashkurse), [LangChain Documentation](https://python.langchain.com/docs/introduction/), [LangGraph Documentation](https://langchain-ai.github.io/langgraph/) and LangChain Video Series.

## Setup

### 1. Create Environment
```bash
python -m venv langchain_env
source langchain_env/bin/activate  # Windows: langchain_env\Scripts\activate
```

### 2. Install Dependencies
```bash
pip install -r requirements.txt
```

### 3. Environment Configuration
Create a `.env` file in the root directory and add the API keys needed:
```bash
OPENAI_API_KEY=your_openai_api_key_here
ANTHROPIC_API_KEY=your_anthropic_api_key_here
GOOGLE_API_KEY=your_google_api_key_here
HUGGINGFACE_API_TOKEN=your_huggingface_token_here
LANGCHAIN_API_KEY=your_langchain_api_key_here
```

## Repository Structure

### Beginner
1. Start with `1_Basics/` - Learn fundamental concepts
2. Move to `2_Chains/` - Understand sequential processing  
3. Explore `3_Memory/` - Add conversation persistence

### Intermediate
4. Master `4_LCEL/` - Modern LangChain patterns
5. Implement `5_RAG/` - Build knowledge systems
6. Practice `6_Tools/` - Integrate external capabilities

### Advanced
7. Develop `7_Agents/` - Create systems
8. Study `additional/` - Production best practices and additional topics like LangSmith
# README Generator

## Description
This project automates the generation of professional README.md files for codebases using advanced natural language processing. It leverages a vector database and the Qwen3:8b model to create structured documentation that includes project overview, installation instructions, usage examples, and more.

## Installation
1. **Install Ollama and Qwen3:8b Model**  
   Follow this guide to set up Ollama and the Qwen3:8b model:  
   [https://www.freecodecamp.org/news/build-a-local-ai/](https://www.freecodecamp.org/news/build-a-local-ai/)

2. **Install Dependencies**  
   Ensure you have Python 3.8+ and the required libraries installed:
   ```bash
   pip install langchain langchain-community chromadb ollama
   ```

3. **Set Up Environment**  
   Create a virtual environment and activate it:
   ```bash
   python -m venv env
   source env/bin/activate  # On Windows: .\env\Scripts\activate
   ```

## Usage
1. Set the `PROJECT_PATH` environment variable to your code directory:
   ```bash
   export PROJECT_PATH=/path/to/your/project
   ```

2. Run the script:
   ```bash
   python generate_readme.py
   ```

3. The generated `README.md` will be saved in your project directory.

## Features
- **Automated Documentation**  
  Creates structured READMEs with project overview, installation, usage, and more.
- **Smart Search**  
  Uses a vector database to retrieve relevant code context for accurate documentation.
- **Model Integration**  
  Leverages the powerful Qwen3:8b model for natural language generation.
- **Customizable Structure**  
  Easily extendable to include additional sections like contributors, license, or changelog.

## Example
Here's a sample of what the generated README might look like:

```
# My Awesome Project

## Description
A brief overview of what your project does...

## Installation
1. Install Ollama and Qwen3:8b model...
2. Clone the repository...
3. Install dependencies...

## Usage
Run the script with:
```bash
python main.py
```

## Features
- Feature 1
- Feature 2
- Feature 3
```

## File / Project Structure
The project includes:
- Python scripts for core functionality
- Jupyter notebooks for analysis and visualization
- Configuration files for model and database setup
- Utility scripts for data processing and reporting

The generated `README.md` will be saved in your project directory, ready for use in your codebase.
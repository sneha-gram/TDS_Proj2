# AI-Powered Academic Assistant API

This API leverages state-of-the-art language models to autonomously interpret, process, and answer queries related to academic content, programming, and data analysis. It seamlessly integrates intelligent question handling, secure code execution, and file-based data extraction.

## How It Works

1. **Understanding the Question:**
   - Analyzes whether the query requires a simple response or computational assistance.
   - Identifies relevant context from existing knowledge.
   
2. **Generating and Executing Code:**
   - Constructs Python or Bash scripts dynamically when needed.
   - Executes scripts in an isolated environment to prevent security risks.
   - Extracts code from markdown syntax when present.

3. **Processing Files for Context:**
   - Accepts ZIP and CSV files to extract relevant data.
   - Uses structured content from files to improve response accuracy.
   
4. **Interfacing with LLMs:**
   - Securely connects to external APIs to generate precise answers.
   - Ensures data security through tokenized authentication.

## Setting Up the API

### Prerequisites:
- Python 3.8 or later
- Required libraries: FastAPI, scikit-learn, python-dotenv

### Installation Guide:

1. **Clone the Repository:**
   ```sh
   git clone https://github.com/sneha-gram/TDS_Proj2.git
   cd TDS_Proj2
   ```

2. **Install Dependencies:**
   ```sh
   pip install -r requirements.txt
   ```

3. **Environment Configuration:**
   - Create a `.env` file with the necessary API credentials:
     ```env
     LLM_API_KEY=your_api_key
     GITHUB_API_KEY=your_api_token_here
     VERCEL_API_KEY=your_api_token_here
     ```

4. **Start the API Server:**
   ```sh
   uvicorn main:app --host 0.0.0.0 --port 8000 --reload
   ```

## Making API Requests

### Endpoint: `/solve`
- **Method:** `POST`
- **Inputs:**
  - `question`: A textual query requiring an answer.
  - `file` (optional): A CSV/ZIP file to enhance contextual understanding.

### Sample Request:
```sh
curl -X POST "http://localhost:8000/solve" \
  -H "Content-Type: multipart/form-data" \
  -F "question=Explain the use of pandas for data manipulation." \
  -F "file=@sample.csv"
```

### Expected Response:
```json
{
  "answer": "Pandas provides tools like DataFrame operations, missing value handling, and indexing for data manipulation.",
  "code": "import pandas as pd\ndf.fillna(method='bfill')"
}
```

## Handling Errors
- Provides clear error messages for incorrect inputs and execution failures.
- Maintains an error log for debugging.

## Contribution Guidelines
- Fork the repository and create a branch.
- Implement and test the feature.
- Submit a pull request with a detailed description.

## License
This project is released under the MIT License.


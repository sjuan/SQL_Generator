# SQL Query Generator

A powerful Jupyter notebook application that leverages OpenAI's GPT-3.5-turbo to automatically generate SQL queries from natural language questions. This tool provides an intuitive web interface built with Gradio, making it easy for users to convert plain English questions into executable SQL queries without writing code.

## 🎯 Project Description

The SQL Query Generator is designed to bridge the gap between natural language and SQL syntax. Simply describe what data you want to retrieve in plain English, and the AI will generate the corresponding SQL query based on your database schema. This is particularly useful for:

- **Non-technical users** who need to query databases without learning SQL
- **Developers** who want to quickly prototype queries
- **Data analysts** who need to generate complex queries faster
- **Learning SQL** by seeing how natural language translates to SQL syntax

The application uses OpenAI's GPT-3.5-turbo model with a carefully crafted system prompt to ensure accurate SQL generation that follows best practices.

## ✨ Features

- 🤖 **AI-Powered SQL Generation**: Uses OpenAI's GPT-3.5-turbo to convert natural language to SQL
- 🌐 **Interactive Web Interface**: Beautiful Gradio UI that runs in your browser
- 🔒 **Secure API Key Management**: Uses environment variables to protect your credentials
- 📊 **Customizable Schema**: Easily modify the database schema to match your needs
- 🎯 **SQLite Compatible**: Generates queries optimized for SQLite databases
- 📝 **Clean Output**: Returns raw SQL queries without markdown formatting

## 📋 Prerequisites

Before running this project, ensure you have:

- **Python 3.7+** installed on your system
- **Jupyter Notebook** or **JupyterLab** installed
- An **OpenAI API key** (get one at [platform.openai.com](https://platform.openai.com))
- Internet connection for API calls

## 🚀 Installation & Setup

### Step 1: Clone the Repository

```bash
git clone https://github.com/sjuan/SQL_Generator.git
cd SQL_Generator
```

### Step 2: Install Required Packages

Install the necessary Python packages using pip:

```bash
pip install openai gradio
```

Alternatively, if you're using a virtual environment (recommended):

```bash
# Create a virtual environment
python -m venv venv

# Activate it (Linux/Mac)
source venv/bin/activate

# Activate it (Windows)
venv\Scripts\activate

# Install packages
pip install openai gradio
```

### Step 3: Set Up Your OpenAI API Key

**For Linux/Mac:**
```bash
export OPENAI_API_KEY="your-api-key-here"
```

**For Windows (Command Prompt):**
```cmd
set OPENAI_API_KEY=your-api-key-here
```

**For Windows (PowerShell):**
```powershell
$env:OPENAI_API_KEY="your-api-key-here"
```

**Permanent Setup (Optional):**

To make the API key persistent across terminal sessions, add it to your shell configuration file:

- **Linux/Mac**: Add `export OPENAI_API_KEY="your-api-key-here"` to `~/.bashrc` or `~/.zshrc`
- **Windows**: Add it to your system environment variables through System Properties

## 📖 How to Run

### Method 1: Using Jupyter Notebook

1. **Open the notebook:**
   ```bash
   jupyter notebook SQL_Generator.ipynb
   ```

2. **Run all cells in order:**
   - The first cell installs dependencies and sets up the OpenAI client
   - The second cell defines the SQL generation function
   - The third cell launches the Gradio web interface

3. **Access the web interface:**
   - After running the third cell, a local URL will be displayed (typically `http://127.0.0.1:7860`)
   - The interface should open automatically in your browser
   - If not, copy and paste the URL into your browser

4. **Start generating SQL queries:**
   - Type your natural language question in the input box
   - Click submit or press Enter
   - The generated SQL query will appear in the output box below

### Method 2: Using JupyterLab

1. **Launch JupyterLab:**
   ```bash
   jupyter lab
   ```

2. **Open `SQL_Generator.ipynb`** from the file browser

3. **Run all cells** using the "Run All Cells" button or by executing each cell sequentially

### Example Queries

Try asking questions like:
- "Show me all customer names from California"
- "What are the total sales for each product category?"
- "List all orders placed in 2024"
- "Find customers who have placed more than 5 orders"
- "Show me the average order amount by state"

## 🗄️ Database Schema

The application is pre-configured to work with the following database schema:

### Products Table
- `ProductID` (INT, Primary Key)
- `Name` (TEXT)
- `Price` (REAL)
- `Category` (TEXT)

### Orders Table
- `OrderID` (INT, Primary Key)
- `CustomerID` (INT, Foreign Key)
- `OrderDate` (TEXT)
- `TotalAmount` (REAL)

### Customers Table
- `CustomerID` (INT, Primary Key)
- `FirstName` (TEXT)
- `LastName` (TEXT)
- `Email` (TEXT)
- `State` (TEXT)

### Customizing the Schema

To use your own database schema, modify the `database_schema` variable in the first cell of the notebook:

```python
database_schema = """
-- Your custom schema here
-- Table: YourTable
-- Columns: Column1 (TYPE), Column2 (TYPE), ...
"""
```

## 🔧 Configuration

### Changing the AI Model

To use a different OpenAI model, modify the `model` parameter in the `generate_sql_query` function:

```python
response = client.chat.completions.create(
    model="gpt-4",  # Change from "gpt-3.5-turbo" to "gpt-4" for better accuracy
    messages=messages,
    temperature=0.0,
    max_tokens=150
)
```

### Adjusting Response Length

Modify the `max_tokens` parameter to allow longer or shorter SQL queries:

```python
max_tokens=300  # Increase for more complex queries
```

## 🔒 Security Best Practices

- ✅ **Never commit API keys** to version control
- ✅ **Use environment variables** to store sensitive information
- ✅ **Keep your API key private** and don't share it
- ✅ **Rotate your API keys** periodically
- ✅ **Monitor your API usage** on the OpenAI dashboard

## 🐛 Troubleshooting

### "OPENAI_API_KEY environment variable is not set"
- Make sure you've exported the API key in your terminal before starting Jupyter
- Verify the key is set by running: `echo $OPENAI_API_KEY` (Linux/Mac) or `echo %OPENAI_API_KEY%` (Windows)

### "API CALL FAILED" Error
- Check your internet connection
- Verify your API key is valid and has sufficient credits
- Ensure you haven't exceeded your API rate limits

### Gradio Interface Won't Launch
- Make sure port 7860 is not already in use
- Try changing the port: `iface.launch(server_port=7861)`

### Import Errors
- Ensure all packages are installed: `pip install openai gradio`
- If using a virtual environment, make sure it's activated

## 📝 License

This project is open source and available for educational and personal use.

## 🤝 Contributing

Contributions, issues, and feature requests are welcome! Feel free to check the issues page or submit a pull request.

## 📧 Support

If you encounter any problems or have questions, please open an issue on the GitHub repository.

---

**Note**: This project requires an active OpenAI API key and will incur API usage costs based on OpenAI's pricing. Make sure to monitor your usage to avoid unexpected charges.


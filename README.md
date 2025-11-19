# SQL Query Generator

A Jupyter notebook application that uses OpenAI's GPT-3.5-turbo to generate SQL queries from natural language questions. Built with Gradio for an interactive web interface.

## Features

- Convert natural language questions into SQL queries
- Interactive web interface using Gradio
- Uses OpenAI's GPT-3.5-turbo model
- Supports SQLite database schema

## Prerequisites

- Python 3.x
- OpenAI API key

## Setup

1. Install required packages:
```bash
pip install openai gradio
```

2. Set your OpenAI API key as an environment variable:
```bash
export OPENAI_API_KEY="your-api-key-here"
```

3. Open and run the `SQL_Generator.ipynb` notebook

## Usage

1. Run all cells in the notebook
2. The Gradio interface will launch automatically
3. Enter your natural language question in the input box
4. The generated SQL query will appear in the output box

## Database Schema

The application is configured to work with the following schema:

- **Products**: ProductID (INT, PK), Name (TEXT), Price (REAL), Category (TEXT)
- **Orders**: OrderID (INT, PK), CustomerID (INT, FK), OrderDate (TEXT), TotalAmount (REAL)
- **Customers**: CustomerID (INT, PK), FirstName (TEXT), LastName (TEXT), Email (TEXT), State (TEXT)

You can modify the `database_schema` variable in the notebook to match your own database structure.

## Security Note

This project uses environment variables to store the API key. Never commit API keys or sensitive information to version control.


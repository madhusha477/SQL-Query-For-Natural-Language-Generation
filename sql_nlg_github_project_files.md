# SQL Query For Natural Language Generation – GitHub Project Files

## Project Title
SQL Query For Natural Language Generation

---

# 1. Project Structure

```bash
sql-query-nlg/
│── app.py
│── requirements.txt
│── README.md
│── templates/
│   └── index.html
│── static/
│   └── style.css
```

---

# 2. app.py

```python
from flask import Flask, render_template, request

app = Flask(__name__)

# Function to convert SQL query into natural language

def sql_to_natural_language(query):
    query = query.lower()

    if "select" in query and "from" in query:
        columns = query.split("from")[0].replace("select", "").strip()
        table = query.split("from")[1].split()[0]

        if "where" in query:
            condition = query.split("where")[1]
            return f"Retrieve {columns} from the {table} table where {condition}."

        return f"Retrieve {columns} from the {table} table."

    elif "insert into" in query:
        table = query.split("insert into")[1].split()[0]
        return f"Insert new data into the {table} table."

    elif "update" in query:
        table = query.split("update")[1].split()[0]
        return f"Update records in the {table} table."

    elif "delete from" in query:
        table = query.split("delete from")[1].split()[0]
        return f"Delete records from the {table} table."

    return "Unable to understand the SQL query."


@app.route('/', methods=['GET', 'POST'])
def index():
    result = ""

    if request.method == 'POST':
        sql_query = request.form['query']
        result = sql_to_natural_language(sql_query)

    return render_template('index.html', result=result)


if __name__ == '__main__':
    app.run(debug=True)
```

---

# 3. templates/index.html

```html
<!DOCTYPE html>
<html>
<head>
    <title>SQL to Natural Language</title>
    <link rel="stylesheet" href="{{ url_for('static', filename='style.css') }}">
</head>
<body>

<div class="container">
    <h1>SQL Query to Natural Language Generator</h1>

    <form method="POST">
        <textarea name="query" placeholder="Enter SQL Query Here"></textarea>
        <br>
        <button type="submit">Generate</button>
    </form>

    <div class="result">
        <h3>Output:</h3>
        <p>{{ result }}</p>
    </div>
</div>

</body>
</html>
```

---

# 4. static/style.css

```css
body {
    font-family: Arial, sans-serif;
    background-color: #f5f5f5;
}

.container {
    width: 60%;
    margin: auto;
    margin-top: 50px;
    background: white;
    padding: 20px;
    border-radius: 10px;
    box-shadow: 0px 0px 10px rgba(0,0,0,0.2);
}

h1 {
    text-align: center;
}

textarea {
    width: 100%;
    height: 120px;
    padding: 10px;
    margin-top: 20px;
}

button {
    padding: 10px 20px;
    background-color: #007bff;
    color: white;
    border: none;
    margin-top: 10px;
    cursor: pointer;
}

button:hover {
    background-color: #0056b3;
}

.result {
    margin-top: 20px;
    background: #e9ecef;
    padding: 15px;
    border-radius: 5px;
}
```

---

# 5. requirements.txt

```txt
Flask==3.0.0
```

---

# 6. README.md

```md
# SQL Query For Natural Language Generation

## Description
This project converts SQL queries into human-readable natural language statements using Python and Flask.

## Features
- Converts SELECT queries
- Converts INSERT queries
- Converts UPDATE queries
- Converts DELETE queries
- Simple web interface

## Technologies Used
- Python
- Flask
- HTML
- CSS

## Installation

```bash
pip install -r requirements.txt
```

## Run the Project

```bash
python app.py
```

## Example

### Input
```sql
SELECT name, age FROM students WHERE age > 18;
```

### Output
Retrieve name, age from the students table where age > 18.
```

---

# 7. GitHub Upload Steps

```bash
git init
git add .
git commit -m "Initial Commit"
git branch -M main
git remote add origin https://github.com/yourusername/sql-query-nlg.git
git push -u origin main
```

---

# 8. LinkedIn Project Description

Developed a SQL Query to Natural Language Generation system using Python and Flask. The application converts SQL statements into human-readable text, improving query understanding for beginners and non-technical users. Implemented support for SELECT, INSERT, UPDATE, and DELETE queries with a responsive web interface.


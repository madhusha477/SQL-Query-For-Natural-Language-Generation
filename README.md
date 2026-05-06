# SQL-Query-For-Natural-Language-Generation
# SQL → Natural Language Generator

A lightweight, single-file web app that converts SQL queries into plain-language explanations using the Anthropic Claude API. No backend, no install, no dependencies — just open the HTML file in a browser.

![SQL to Natural Language Generator](https://img.shields.io/badge/Powered%20by-Claude%20API-blueviolet) ![License](https://img.shields.io/badge/license-MIT-green) ![HTML](https://img.shields.io/badge/built%20with-HTML%2FJS-orange)

---

## Demo

> **Input SQL:**
> ```sql
> SELECT c.name, SUM(o.amount) AS total_spent
> FROM customers c
> JOIN orders o ON c.id = o.customer_id
> WHERE o.created_at >= '2024-01-01'
> GROUP BY c.name
> ORDER BY total_spent DESC
> LIMIT 10;
> ```
>
> **Output (Plain English):**
> This query finds the top 10 customers by total amount spent since January 1, 2024. It joins the customers and orders tables, sums up each customer's order amounts, and returns the results sorted from highest to lowest spender.

---

## Features

- **Natural language output** — converts any SQL into a human-readable explanation
- **4 tone modes** — Plain English, Business summary, Technical, Simple (non-technical)
- **SQL dialect support** — PostgreSQL, MySQL, SQLite, BigQuery, SQL Server, Oracle
- **Schema context** — optionally provide table/column descriptions for better accuracy
- **Copy to clipboard** — one-click copy of the generated explanation
- **Keyboard shortcut** — `Ctrl + Enter` / `Cmd + Enter` to run
- **Dark mode** — automatically adapts to system preference
- **Zero dependencies** — single HTML file, no frameworks, no npm

---

## Getting Started

### Option 1 — Open locally

1. Clone or download this repository
2. Open `sql_to_natural_language.html` in any modern browser
3. Enter your [Anthropic API key](https://console.anthropic.com)
4. Paste your SQL and click **Generate explanation**

```bash
git clone https://github.com/your-username/sql-to-natural-language.git
cd sql-to-natural-language
open sql_to_natural_language.html   # macOS
# or double-click the file on Windows/Linux
```

### Option 2 — Host on GitHub Pages

1. Fork or push this repo to GitHub
2. Go to **Settings → Pages**
3. Set source to `main` branch, `/ (root)`
4. Your app will be live at `https://your-username.github.io/sql-to-natural-language/sql_to_natural_language.html`

---

## Requirements

| Requirement | Details |
|---|---|
| Browser | Any modern browser (Chrome, Firefox, Safari, Edge) |
| API Key | [Anthropic API key](https://console.anthropic.com) — free tier available |
| Internet | Required to call the Claude API |
| Server / Backend | None needed |

---

## API Key & Privacy

- Your API key is entered in the browser and **never stored** — it lives in memory for that session only
- SQL queries are sent **only to Anthropic's API** and are not logged or stored by this app
- Anthropic's data handling is governed by their [Privacy Policy](https://www.anthropic.com/privacy)

---

## File Structure

```
sql-to-natural-language/
├── sql_to_natural_language.html   # The entire app — HTML + CSS + JS in one file
└── README.md
```

---

## Customization

All logic lives in `sql_to_natural_language.html`. Common things to change:

| What | Where |
|---|---|
| Claude model | `model: 'claude-sonnet-4-20250514'` in the fetch call |
| Add a new tone | Add an `<option>` in the tone `<select>` and a matching entry in `toneMap` |
| Change max output length | Adjust `max_tokens: 1000` |
| Pre-fill API key | Set `value="sk-ant-..."` on the `#apiKey` input (not recommended for public repos) |

---

## How It Works

```
User pastes SQL
      ↓
App builds a prompt with tone + dialect + schema context + SQL
      ↓
POST https://api.anthropic.com/v1/messages  (claude-sonnet-4-20250514)
      ↓
Claude returns a natural language explanation
      ↓
Result displayed with copy button
```

---

## Example Use Cases

- **Developers** — quickly understand legacy SQL written by others
- **Data analysts** — document queries for non-technical stakeholders
- **Business users** — understand what a report query actually does
- **Students** — learn SQL by seeing queries explained in plain English
- **Code reviewers** — add auto-generated comments to SQL files

---

## License

MIT — free to use, modify, and distribute. See [LICENSE](LICENSE) for details.

---

## Contributing

Pull requests are welcome! For major changes, please open an issue first to discuss what you'd like to change.

1. Fork the repo
2. Create a feature branch (`git checkout -b feature/my-feature`)
3. Commit your changes (`git commit -m 'Add my feature'`)
4. Push to the branch (`git push origin feature/my-feature`)
5. Open a Pull Request

---

## Acknowledgements

- Built By Madhusha Velpula
  

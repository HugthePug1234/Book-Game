# Book Generator Web

A web-based Flask application to generate customizable books. Users can add characters, set book details, generate a plot, preview the structure, and produce a full book (100–400 pages, 10–100 chapters) displayed on-screen and downloadable as Markdown.

## Features
- Add characters with detailed attributes (name, age, gender, occupation, etc.) and relationships.
- Customize book details (genre, setting, tone, themes, page count, chapter count, conflict intensity, title, key plot points).
- Generate a plot based on characters and settings.
- Preview the book structure with chapter outlines.
- Generate a complete book with a narrative arc, viewable in the browser and downloadable as Markdown.
- Responsive, user-friendly interface with error handling.

## Prerequisites
- Python 3.8+
- Git

## Setup (Local)
1. Clone the repository:
   ```bash
   git clone https://github.com/your-username/book-generator-web.git
   cd book-generator-web
   ```
2. Create a virtual environment:
   ```bash
   python -m venv venv
   source venv/bin/activate  # On Windows: venv\Scripts\activate
   ```
3. Install dependencies:
   ```bash
   pip install -r requirements.txt
   ```
4. Create the output directory:
   ```bash
   mkdir output
   touch output/.gitkeep
   ```
5. Run the application:
   ```bash
   python app.py
   ```
6. Open `http://127.0.0.1:5000` in a browser.

## Alternative Hosting Options
If you want to host the app publicly without Heroku, consider:
- **Render**:
  1. Sign up at `https://render.com`.
  2. Create a new web service, connect your GitHub repository.
  3. Set:
     - Build Command: `pip install -r requirements.txt`
     - Start Command: `gunicorn app:app`
  4. Deploy and access the provided URL.
- **Railway**:
  1. Sign up at `https://railway.app`.
  2. Create a new project, link your repository.
  3. Configure to use Python and set `gunicorn app:app` as the start command.
  4. Deploy and use the generated URL.
- **Personal Server**:
  1. Set up a server with Python and Gunicorn.
  2. Clone the repository, install dependencies.
  3. Run `gunicorn --workers 3 --bind 0.0.0.0:8000 app:app`.
  4. Access via your server’s IP or domain (e.g., `http://your-server-ip:8000`).
- **Note**: GitHub Pages is not suitable, as it only serves static files and cannot run Flask apps.

## Project Structure
```
book-generator-web/
├── app.py
├── templates/
│   ├── index.html
│   ├── add_character.html
│   ├── set_details.html
│   └── book_display.html
├── static/
│   └── style.css
├── output/
│   └── .gitkeep
├── requirements.txt
├── .gitignore
└── README.md
```

## Usage
1. Navigate to the home page (`http://127.0.0.1:5000` locally).
2. Use the navigation to:
   - **Add Character**: Enter details (Name and Age required).
   - **Set Book Details**: Specify book attributes (most fields required).
   - **Generate Plot**: Create a plot summary.
   - **Preview Structure**: View the book outline.
   - **Generate Book**: Produce the full book, displayed on a dedicated page.
3. On the book display page, view the book and download it as a Markdown file.
4. Errors and success messages appear on the home page.

## Troubleshooting
- **404 Errors**:
  - Ensure `templates/` contains `index.html`, `add_character.html`, `set_details.html`, `book_display.html`.
  - Verify `static/` contains `style.css`.
  - Check file names are lowercase (e.g., `style.css`, not `Style.css`).
  - Run `ls -R` to confirm structure:
    ```
    .:
    app.py  output  README.md  requirements.txt  static  templates  .gitignore

    ./output:
    .gitkeep

    ./static:
    style.css

    ./templates:
    add_character.html  book_display.html  index.html  set_details.html
    ```
  - If local, ensure `python app.py` is running and access `http://127.0.0.1:5000`.
  - If deployed, check server logs for “TemplateNotFound” or file errors.
- **Blank or unstyled page**:
  - Verify `static/style.css` exists.
  - Check browser console (F12 > Console) for errors.
  - Ensure `app.py` has `static_folder='static'`.
- **Book not generating**:
  - Add at least 2 characters and set book details first.
  - Check homepage output for errors (e.g., “At least 2 characters required”).
- **Git issues**:
  - Ensure all files are committed:
    ```bash
    git add .
    git commit -m "Setup project"
    git push origin main
    ```

## License
MIT License. See `LICENSE` file (not included in this template).

## Contributing
Fork the repository, make changes, and submit a pull request.
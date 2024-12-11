Thanks for providing the details. Here's an updated version of the `README.md`, taking into account the fact that the Django admin interface is enabled and accessible through the `/admin/` URL. I'll also highlight the account creation and login processes in the updated version.

---

# Django YouTube Blog Generator

This Django application generates and publishes blog articles automatically to WordPress using YouTube videos as input. By transcribing video content, leveraging ChatGPT, and using document formatting tools, it creates SEO-friendly articles tailored to specific topics.

---

## Key Features

1. **YouTube Video Transcription**:
   - Downloads and converts the audio of the video.
   - Uses the AssemblyAI API to extract readable text.

2. **Automated Article Generation**:
   - Creates outlines and full articles using ChatGPT (GPT-4 model).
   - Advanced formatting (HTML and DOCX) for publication.

3. **WordPress Integration**:
   - Connects to a WordPress site via JWT to publish articles automatically.

4. **User Management**:
   - Authentication and account management for users.
   - Personalized view for users to list their generated articles.

5. **Admin Interface**:
   - Access to Django's admin panel for managing database entries and monitoring the application.

---

## Prerequisites

1. Python 3.9 or later.
2. Python virtual environment (`venv` or equivalent).
3. SQLite database (preconfigured).
4. Required API keys:
   - OpenAI (ChatGPT).
   - AssemblyAI (audio transcription).
   - WordPress JWT credentials.

---

## Installation

1. Clone the repository:
   ```bash
   git clone <REPOSITORY_URL>
   cd <PROJECT_NAME>
   ```

2. Create a virtual environment and activate it:
   ```bash
   python -m venv env
   source env/bin/activate  # On Windows, use `env\Scripts\activate`
   ```

3. Install the dependencies:
   ```bash
   pip install -r requirements.txt
   ```

4. Configure environment variables:
   - Rename `.env.example` to `.env` and add your API keys:
     ```
     OPENAI_API_KEY=<your_openai_api_key>
     ASSEMBLYAI_API_KEY=<your_assemblyai_api_key>
     WORDPRESS_URL=<your_wordpress_site_url>
     WORDPRESS_USERNAME=<your_username>
     WORDPRESS_PASSWORD=<your_password>
     ```

5. Apply database migrations:
   ```bash
   python manage.py migrate
   ```

6. Create a superuser for accessing the Django admin interface:
   ```bash
   python manage.py createsuperuser
   ```

7. Launch the development server:
   ```bash
   python manage.py runserver
   ```

---

## Usage

### 1. Accessing the Application
- Open your web browser and navigate to `http://127.0.0.1:8000/`.

### 2. Admin Panel
- Access the Django admin interface at `http://127.0.0.1:8000/admin/`.
- Use the superuser account created during the installation to log in.

### 3. User Registration and Login
- Users can sign up and log in via the provided frontend views:
  - **Signup**: Accessible at `/signup/`.
  - **Login**: Accessible at `/login/`.
- Once logged in, users can manage their generated articles.

### 4. Generating Blog Articles
- Provide a YouTube video link, a keyword, and a subject in the designated input fields.
- The app will:
  1. Transcribe the video content.
  2. Generate an article outline and the full article using ChatGPT.
  3. Format the article and publish it to WordPress.

---

## Deployment

To deploy this application in a production environment:

1. **Set up a production server**:
   - Use a web server like Nginx or Apache.
   - Use Gunicorn or uWSGI to serve the Django application.

2. **Set up a production database**:
   - Configure a PostgreSQL database for better scalability.

3. **Configure environment variables**:
   - Make sure the `.env` file contains the correct production credentials.

4. **Set up HTTPS**:
   - Use Let's Encrypt or another SSL provider for secure connections.

5. **Run migrations and collect static files**:
   ```bash
   python manage.py migrate
   python manage.py collectstatic
   ```

6. **Monitor the application**:
   - Use tools like Supervisor or systemd to keep the application running.

---

## API Overview

### Endpoint: `POST /generate-blog-text/`
- **Description**: Generates a blog article using YouTube video transcription.
- **Request Body**:
  ```json
  {
    "link": "<youtube_video_url>",
    "keyword": "<focus_keyword>",
    "subject": "<article_subject>"
  }
  ```
- **Response**:
  ```json
  {
    "content": "<generated_article_content>",
    "outlines": "<article_outlines>"
  }
  ```

---

## Technologies Used

- **Django**: Backend framework.
- **OpenAI API**: For generating blog content and outlines.
- **AssemblyAI API**: For YouTube video transcription.
- **WordPress REST API**: For publishing articles.
- **Bootstrap**: Frontend styling.

---

## Contributing

Feel free to fork the repository and submit pull requests for enhancements or bug fixes.

---

## License

This project is licensed under the MIT License.

---

This version includes the admin interface and instructions for account creation and login processes. Let me know if you'd like to refine or expand further!

# Experiment 8: Session Tracking Mechanism

**Skill Development Course — Node.js / React.js / Django Lab Manual**

A practical demonstration of session tracking in web applications using **Cookies** and **Flask Sessions** in Python.

## 📌 Overview

HTTP is a stateless protocol, meaning each request is treated independently by default. A web application does not automatically remember a user's previous interactions when another request is made.

Session tracking helps web applications maintain information across multiple requests. It is commonly used to remember user preferences, track visits, manage login states, and personalize the user experience.

This project demonstrates two approaches to session tracking:

- **Cookie-based tracking:** Stores a user's language preference in a browser cookie.
- **Session-based tracking:** Maintains a visit counter using Flask's session interface.

The project contains two simple Flask applications that illustrate how information can be preserved across requests.

## 🎯 Aim

To understand and implement session tracking in web applications using cookies and HTTP sessions, and to observe how user-specific information is maintained across multiple HTTP requests.

## 📚 Learning Objectives

By completing this experiment, you will learn how to:

- Understand the stateless nature of HTTP.
- Create and retrieve browser cookies using Flask.
- Maintain user-specific values using Flask sessions.
- Build routes and render dynamic HTML templates.
- Test persistence of information across multiple requests.
- Compare cookie-based tracking with Flask's default session mechanism.
- Understand basic security considerations when handling cookies and sessions.

## 🛠️ Technologies Used

| Technology | Purpose |
|---|---|
| Python | Backend programming language |
| Flask | Lightweight Python web framework |
| HTML | Structure of web pages |
| Jinja2 | Dynamic HTML template rendering |
| HTTP Cookies | Store small pieces of information in the browser |
| Flask Sessions | Maintain user-specific state across requests |

## 📂 Project Structure

```text
Session-tracking-mechanism/
│
├── app_cookies.py
├── app_session.py
├── requirements.txt
├── Experiment_08_Session_Tracking.docx
└── README.md
```

### File Descriptions

| File | Description |
|---|---|
| `app_cookies.py` | Implements cookie-based tracking of a user's language preference. |
| `app_session.py` | Implements visit counting using Flask's session interface. |
| `requirements.txt` | Lists the Python dependencies required to run the project. |
| `Experiment_08_Session_Tracking.docx` | Contains the experiment's lab-manual instructions, code, and expected output. |
| `README.md` | Documents the project, installation, execution, and testing procedures. |

**Note:** The Python applications may use HTML templates. If the code references a `templates/` directory, ensure that the required template files are present in that directory before running the applications.

## ⚙️ Prerequisites

Before running this project, make sure you have:

- Python 3 installed.
- `pip`, the Python package installer.
- A modern web browser.
- A terminal or command prompt.
- Basic knowledge of Python and HTML.

Check your Python installation:

```bash
python --version
```

Check that pip is available:

```bash
python -m pip --version
```

Depending on your system, you may need to use `python3` instead of `python`.

## 🚀 Installation and Setup

### Step 1: Clone the repository

```bash
git clone https://github.com/sushi5456/Session-tracking-mechanism.git
```

### Step 2: Navigate to the project directory

```bash
cd Session-tracking-mechanism
```

### Step 3: Create a virtual environment (recommended)

On Windows:

```bash
python -m venv .venv
.venv\Scripts\activate
```

On macOS or Linux:

```bash
python3 -m venv .venv
source .venv/bin/activate
```

### Step 4: Install dependencies

```bash
python -m pip install -r requirements.txt
```

The application uses Flask as its web framework.

## 🍪 Part A: Cookie-Based Session Tracking

### Objective

To store and retrieve a user's language preference using an HTTP cookie.

### How It Works

1. The user opens the application in a browser.
2. Flask checks whether a cookie named `user_language` exists.
3. If the cookie exists, the application reads and displays its value.
4. If the cookie does not exist, the application indicates that no language preference has been set.
5. The user selects a language, such as English or Spanish.
6. Flask sends a response containing the updated cookie.
7. The browser stores the cookie and sends it with subsequent requests to the same site.
8. The application reads the cookie and displays the saved preference.

### Run the Application

```bash
python app_cookies.py
```

Open the following address in your browser:

http://127.0.0.1:5000/

### Testing Procedure

1. Open the application in your browser.
2. Observe the initial language preference message.
3. Select the option to set the language to English.
4. Return to the home page and verify that the saved language is displayed.
5. Repeat the procedure for Spanish.
6. Inspect the browser's developer tools under **Application/Storage → Cookies** to observe the stored cookie.

### Expected Result

The selected language preference is stored in a browser cookie and can be retrieved on subsequent requests.

**Important:** This example demonstrates storing a language preference. It does not necessarily translate the page into the selected language.

## 🔐 Part B: Session-Based Tracking Using Flask

### Objective

To maintain a visit counter across multiple HTTP requests using Flask's `session` object.

### How It Works

1. The user opens the application.
2. Flask retrieves the existing `visit_count` value from the session.
3. If no value exists, the counter starts at zero.
4. The application increments the counter by one.
5. The updated count is saved in the session.
6. The visit count is displayed on the web page.
7. When the user refreshes the page, the counter increases again.

### Run the Application

If the cookie application is running, stop it using `Ctrl + C`.

Then execute:

```bash
python app_session.py
```

Open the following address:

http://127.0.0.1:5000/

### Testing Procedure

1. Open the application in a fresh browser session.
2. Observe the initial visit count.
3. Refresh the page several times.
4. Verify that the visit count increases with each request.
5. Open the application in a separate browser or private window.
6. Compare the visit counts between the browser sessions.

### Expected Result

The application maintains and displays an increasing visit count across requests associated with the same browser session.

### Understanding Flask Sessions

Flask provides a built-in `session` object for storing user-specific information across requests.

By default, Flask stores session data in a **signed browser cookie**. The signature helps detect tampering, but it does not encrypt the cookie's contents.

For a classroom demonstration, a simple secret key may be used:

```python
app.secret_key = 'super_secret_key'
```

For real applications, replace this example with a securely generated secret key stored outside the source code.

## 🔍 Cookies vs. Flask Sessions

| Feature | Cookies | Flask Sessions |
|---|---|---|
| Purpose in this project | Store language preference | Track the number of visits |
| Access method | `request.cookies` | `session` |
| Set/update method | `response.set_cookie()` | Assign a value to `session` |
| Default storage | Browser | Signed cookie in the browser |
| Persistence | Depends on cookie settings and browser behavior | Depends on session cookie settings and browser behavior |
| Typical applications | Preferences, simple identifiers | User-specific state, temporary workflow data |
| Security consideration | Avoid storing sensitive information directly | Protect the secret key and avoid sensitive session contents |

**Technical note:** Flask's default session implementation is cookie-based. It is not the same as a server-side session store. Server-side sessions can be implemented using an appropriate extension or custom storage backend.

## 🧪 Experiment Summary

| Experiment | Implementation | Expected Outcome |
|---|---|---|
| Cookie tracking | Save a language preference | Preference is displayed on subsequent requests |
| Session tracking | Increment a visit counter | Counter increases on page refresh |
| Browser testing | Use separate browser sessions | Session-specific behavior can be observed |

## 🐛 Troubleshooting

### 1. Flask module not found

**Error:**

```text
ModuleNotFoundError: No module named 'flask'
```

**Solution:**

```bash
python -m pip install -r requirements.txt
```

Make sure your virtual environment is activated if you created one.

### 2. Port 5000 is already in use

Stop the other Flask application using `Ctrl + C` before starting the next application. Both examples use port 5000 by default.

### 3. Cookie value is not updating

- Return to the home page after setting the preference.
- Ensure your browser accepts cookies.
- Check the cookie in the browser's developer tools.
- Clear old cookies if necessary.

### 4. Visit counter resets

The counter may reset if you clear the browser cookies, use a new private browsing session, or otherwise lose the session cookie.

### 5. HTML template cannot be found

If the application uses `render_template()`, ensure the referenced HTML files exist inside Flask's `templates/` directory and that you are running the application from the correct project setup.

## 🔒 Security Considerations

This project is intended for educational purposes.

- Do not use Flask's development server as a production server.
- Do not enable Flask debug mode in a production deployment.
- Use a strong, randomly generated secret key.
- Keep secret keys and credentials out of public repositories.
- Do not store passwords or other sensitive information in browser cookies.
- Remember that Flask's default session cookie is signed, not encrypted.
- Configure cookie security attributes, including `Secure`, `HttpOnly`, and `SameSite`, appropriately for a real deployment.
- Use HTTPS when deploying a web application publicly.

## 🏁 Conclusion

This experiment demonstrates two common mechanisms for maintaining user-related state across HTTP requests: browser cookies and Flask sessions.

The cookie-based application stores and retrieves a language preference, while the session-based application tracks the number of visits. Through these implementations, the experiment illustrates the stateless nature of HTTP and how web applications can preserve user-specific information between requests.

The experiment also introduces the differences between browser cookies and Flask's default session mechanism, along with basic security practices for building web applications.

## 📖 References

- [Flask Documentation](https://flask.palletsprojects.com/)
- [Flask Quickstart — Sessions](https://flask.palletsprojects.com/en/stable/quickstart/#sessions)
- [MDN Web Docs — HTTP Cookies](https://developer.mozilla.org/en-US/docs/Web/HTTP/Cookies)
- [Project Repository](https://github.com/sushi5456/Session-tracking-mechanism)

---

**Experiment:** 8 — Session Tracking Mechanism  
**Course:** Skill Development Course — Node.js / React.js / Django Lab Manual  
**Implementation:** Python and Flask

# Random Password Generator

Welcome to the Random Password Generator and User Login Interface project! This project combines the convenience of a random password generator with a user-friendly login interface, implemented using Python and Flask.

## Project Preview

![Screenshot 2023-08-21 155152](https://github.com/yogesh-hack/Random-Password-generator-python-project/assets/83384315/e765accf-78b8-4560-a1a2-534f47673b27)

Certainly! Create a simple web application using Flask to generate random passwords based on user-defined length:

1. Install Flask if you haven't already:
```bash
pip install Flask
```

2. Create a file named `app.py`:

```python
from flask import Flask, render_template, request
import random
import string

app = Flask(__name__)

def generate_password(length=12):
    characters = string.ascii_letters + string.digits + string.punctuation
    password = ''.join(random.choice(characters) for _ in range(length))
    return password

@app.route('/', methods=['GET', 'POST'])
def index():
    generated_password = ''
    if request.method == 'POST':
        password_length = int(request.form.get('password_length', 12))
        generated_password = generate_password(password_length)
    return render_template('index.html', generated_password=generated_password)

if __name__ == "__main__":
    app.run(debug=True)
```

3. Create a `templates` folder in the same directory as `app.py` and create a file named `index.html` inside the `templates` folder:

```html
<!DOCTYPE html>
<html>
<head>
    <title>Random Password Generator</title>
</head>
<body>
    <h1>Random Password Generator</h1>
    <form method="POST" action="/">
        <label for="password_length">Password Length:</label>
        <input type="number" id="password_length" name="password_length" value="12" min="1"><br><br>
        <input type="submit" value="Generate">
    </form>
    {% if generated_password %}
    <h2>Generated Password:</h2>
    <p>{{ generated_password }}</p>
    {% endif %}
</body>
</html>
```

4. Run the Flask application:
In your terminal, navigate to the directory where `app.py` is located and run the following command:

```bash
python app.py
```

5. Open your web browser and go to `http://127.0.0.1:5000/` to access the password generator web application. You can enter the desired password length and click the "Generate" button to see the generated password.

This Flask application uses HTML templates to render the web page and allows users to input the desired password length. When the form is submitted, the Flask route `index()` is triggered, and the generated password is displayed on the same page.
## Getting Started

To run the project locally:

1. Clone this repository: `git clone https://github.com/yogesh-hack/Random-Password-Generator-python-project.git`
2. Navigate to the project directory: `cd random-password-generator`
3. Install dependencies: `pip install -r requirements.txt`
4. Run the application: `python app.py`

## Contributing

Contributions are welcome! If you have ideas for improvements, bug fixes, or new features, feel free to open an issue or submit a pull request.

---

Made with ❤️ by [Yogesh Baghel](https://github.com/yogesh-hack)



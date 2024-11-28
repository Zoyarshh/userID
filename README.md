</head>
<body>
    <div class="container">
        <h2>Register</h2>
        <form>
            <input type="text" id="registerUserID" placeholder="User ID" required>
            <input type="email" id="registerEmail" placeholder="Email" required>
            <input type="password" id="registerPassword" placeholder="Password" required>
            <button type="button" onclick="register()">Register</button>
        </form>
    </div>

    <script>
        function register() {
            const userID = document.getElementById('registerUserID').value;
            const email = document.getElementById('registerEmail').value;
            const password = document.getElementById('registerPassword').value;
            localStorage.setItem('userID', userID);
            localStorage.setItem('email', email);
            localStorage.setItem('password', password);
            alert('Registered successfully!');
            window.close();
            window.opener.openPopup('login.html');
        }
    </script>
</body>
</html>

<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Login</title>
    <link rel="stylesheet" href="styles.css">
</head>
<body>
    <div class="container">
        <h2>Login</h2>
        <form>
            <input type="text" id="loginUserID" placeholder="User ID" required>
            <input type="password" id="loginPassword" placeholder="Password" required>
            <button type="button" onclick="login()">Login</button>
        </form>
    </div>

    <script>
        function login() {
            const userID = document.getElementById('loginUserID').value;
            const password = document.getElementById('loginPassword').value;
            const storedUserID = localStorage.getItem('userID');
            const storedPassword = localStorage.getItem('password');
            if (userID === storedUserID && password === storedPassword) {
                alert('Logged in successfully!');
                window.close();
                window.opener.openPopup('profile.html');
            } else {
                alert('Invalid login credentials!');
            }
        }
    </script>
</body>
</html>

<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Profile</title>
    <link rel="stylesheet" href="styles.css">
</head>
<body>
    <div class="container">
        <h2>Your Profile</h2>
        <p id="profileUserID"></p>
        <p id="profileEmail"></p>
        <button type="button" onclick="logout()">Logout</button>
    </div>

    <script>
        window.onload = function() {
            const userID = localStorage.getItem('userID');
            const email = localStorage.getItem('email');
            document.getElementById('profileUserID').textContent = `User ID: ${userID}`;
            document.getElementById('profileEmail').textContent = `Email: ${email}`;
        }

        function logout() {
            alert('Logged out successfully!');
            window.close();
            window.opener.openPopup('login.html');
        }
    </script>
</body>
</html>



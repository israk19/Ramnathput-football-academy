from zipfile import ZipFile
import os

# Create the HTML content
html_content = """<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0" />
  <title>Ramnathpur Football Academy - Player Registration</title>
  <style>
    body {
      font-family: Arial, sans-serif;
      background-color: #f0f4f8;
      margin: 0;
      padding: 0;
    }
    .container {
      max-width: 600px;
      margin: 40px auto;
      background: white;
      padding: 20px;
      border-radius: 10px;
      box-shadow: 0 0 10px rgba(0,0,0,0.1);
    }
    .logo {
      text-align: center;
      margin-bottom: 20px;
    }
    .logo img {
      max-width: 150px;
    }
    h2 {
      text-align: center;
      color: #003366;
    }
    form {
      display: flex;
      flex-direction: column;
    }
    label {
      margin-top: 10px;
      font-weight: bold;
    }
    input, select, textarea {
      padding: 10px;
      margin-top: 5px;
      border: 1px solid #ccc;
      border-radius: 5px;
    }
    button {
      margin-top: 20px;
      padding: 10px;
      background-color: #003366;
      color: white;
      border: none;
      border-radius: 5px;
      cursor: pointer;
    }
    button:hover {
      background-color: #0055a5;
    }
  </style>
</head>
<body>
  <div class="container">
    <div class="logo">
      <img src="logo.png" alt="Ramnathpur Football Academy Logo">
    </div>
    <h2>Player Registration Form</h2>
    <form action="#" method="POST">
      <label for="name">Full Name</label>
      <input type="text" id="name" name="name" required>

      <label for="dob">Date of Birth</label>
      <input type="date" id="dob" name="dob" required>

      <label for="position">Preferred Position</label>
      <select id="position" name="position">
        <option value="goalkeeper">Goalkeeper</option>
        <option value="defender">Defender</option>
        <option value="midfielder">Midfielder</option>
        <option value="forward">Forward</option>
        <option value="left-winger">Left Winger</option>
        <option value="right-winger">Right Winger</option>
      </select>

      <label for="experience">Football Experience</label>
      <textarea id="experience" name="experience" rows="4"></textarea>

      <label for="contact">Contact Number</label>
      <input type="tel" id="contact" name="contact" required>

      <label for="address">Address</label>
      <textarea id="address" name="address" rows="3"></textarea>

      <button type="submit">Submit Registration</button>
    </form>
  </div>
</body>
</html>
"""

# Create a directory and save the HTML file and image
output_dir = "/mnt/data/ramnathpur_website"
os.makedirs(output_dir, exist_ok=True)

html_file_path = os.path.join(output_dir, "index.html")
with open(html_file_path, "w", encoding="utf-8") as f:
    f.write(html_content)

# Copy the uploaded logo image
logo_path = "/mnt/data/d03db222-3f81-402a-83d1-72d214d8a31f.png"
logo_output_path = os.path.join(output_dir, "logo.png")
os.rename(logo_path, logo_output_path)

# Create ZIP file
zip_path = "/mnt/data/ramnathpur_football_academy_website.zip"
with ZipFile(zip_path, 'w') as zipf:
    zipf.write(html_file_path, "index.html")
    zipf.write(logo_output_path, "logo.png")

zip_path

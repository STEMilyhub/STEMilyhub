# Let's generate a simple HTML and CSS template for the requested website structure.
# Structure:
# - index.html (Home)
# - about.html (About)
# - reviewers.html (Reviewers)
# - videos.html (Videos)
# - contact.html (Contact)
# Minimalist design, with red and blue as the primary colors.

html_template = """
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>{title}</title>
    <link rel="stylesheet" href="styles.css">
</head>
<body>
    <header>
        <nav>
            <ul>
                <li><a href="index.html">Home</a></li>
                <li><a href="about.html">About</a></li>
                <li><a href="reviewers.html">Reviewers</a></li>
                <li><a href="videos.html">Videos</a></li>
                <li><a href="contact.html">Contact</a></li>
            </ul>
        </nav>
    </header>

    <main>
        <section class="content">
            <h1>{heading}</h1>
            <p>{content}</p>
        </section>
    </main>

    <footer>
        <p>&copy; 2024 Academic Support. All Rights Reserved.</p>
    </footer>
</body>
</html>
"""

# Generating five pages (index, about, reviewers, videos, contact).
pages = {
    "index.html": {
        "title": "Home - Academic Support",
        "heading": "Welcome to Academic Support!",
        "content": "Helping future G11 STEM students excel through curated reviewers and educational videos."
    },
    "about.html": {
        "title": "About Us - Academic Support",
        "heading": "About Academic Support",
        "content": "We are dedicated to guiding future G11 STEM students with high-quality reviewers and video lessons."
    },
    "reviewers.html": {
        "title": "Reviewers - Academic Support",
        "heading": "STEM Reviewers",
        "content": "Explore our collection of reviewers tailored to help you succeed in your STEM subjects."
    },
    "videos.html": {
        "title": "Videos - Academic Support",
        "heading": "Educational Videos",
        "content": "Watch video tutorials and lessons designed to strengthen your understanding of complex topics."
    },
    "contact.html": {
        "title": "Contact Us - Academic Support",
        "heading": "Get in Touch",
        "content": "Have questions or feedback? Contact us at: support@academicsupport.com"
    }
}

# Basic CSS for a minimalist, red-and-blue-themed website.
css_content = """
body {
    font-family: 'Arial', sans-serif;
    margin: 0;
    padding: 0;
    background-color: #f4f4f4;
    color: #333;
}

header {
    background-color: #0044cc;
    color: white;
    padding: 1rem;
    text-align: center;
}

nav ul {
    list-style: none;
    padding: 0;
}

nav ul li {
    display: inline;
    margin: 0 10px;
}

nav a {
    color: white;
    text-decoration: none;
    font-weight: bold;
}

.content {
    margin: 20px;
    padding: 20px;
    background-color: white;
    border-radius: 5px;
    box-shadow: 0 0 10px rgba(0, 0, 0, 0.1);
}

footer {
    text-align: center;
    padding: 10px;
    background-color: #cc0000;
    color: white;
    position: fixed;
    bottom: 0;
    width: 100%;
}
"""

# Create the necessary files and save them to a ZIP.
import os
from zipfile import ZipFile

output_dir = "/mnt/data/academic_support_website"
os.makedirs(output_dir, exist_ok=True)

# Save the HTML files.
for filename, content in pages.items():
    with open(os.path.join(output_dir, filename), "w") as f:
        f.write(html_template.format(**content))

# Save the CSS file.
with open(os.path.join(output_dir, "styles.css"), "w") as f:
    f.write(css_content)

# Create a ZIP file containing the website files.
zip_path = "/mnt/data/academic_support_website.zip"
with ZipFile(zip_path, 'w') as zipf:
    for root, _, files in os.walk(output_dir):
        for file in files:
            zipf.write(os.path.join(root, file), arcname=file)

zip_path



## Welcome to My Website

This site provides a collection of resources and tools to enhance your understanding and experience in various topics, including GMRS radio operation, education, and technology.

---

### Featured Sections

<div style="display: flex; justify-content: space-between;">
    <ul style="width: 20%; list-style-type: none; padding: 0;">
        <li><a href="#" onclick="changeIframe('GMRS_Channel_Tones.md')">GMRS Channel Tones</a></li>
        <li><a href="#" onclick="changeIframe('chirp.md')">CHIRP Programming</a></li>
        <li><a href="#" onclick="changeIframe('commands.md')">Command Reference</a></li>
        <li><a href="#" onclick="changeIframe('education.md')">Education</a></li>
        <li><a href="#" onclick="changeIframe('forecast.md')">Weather Forecasting</a></li>
        <li><a href="#" onclick="changeIframe('harden.md')">System Hardening</a></li>
        <li><a href="#" onclick="changeIframe('pi_backup.md')">Pi Backup</a></li>
        <li><a href="#" onclick="changeIframe('links.md')">Useful Links</a></li>
    </ul>

    <iframe id="content-frame" src="GMRS_Channel_Tones.md" title="Content Viewer" style="width: 75%; height: 400px; border: none; background-color: #121212; color: #ffffff;"></iframe>
</div>

<script>
function changeIframe(page) {
    document.getElementById('content-frame').src = page;
}
</script>

---

### Styling and Layout

This site uses a minimalist dark theme for better readability and reduced eye strain. The navigation is simplified, and tables are formatted for easy access to key information.

---

### Get Started

Explore the content by navigating through the embedded frame above. Each section provides focused, actionable insights and tools to help you in various aspects of technology and communication.

---

#### Contact
For suggestions or queries, feel free to reach out through the provided contact options.

<style>
body {
    background-color: #121212;
    color: #ffffff;
    font-family: Arial, sans-serif;
    line-height: 1.6;
    padding: 20px;
}
a {
    color: #1e90ff;
    text-decoration: none;
}
a:hover {
    text-decoration: underline;
}
table {
    width: 100%;
    border-collapse: collapse;
    margin: 20px 0;
}
th, td {
    border: 1px solid #333;
    padding: 10px;
    text-align: left;
}
th {
    background-color: #1e1e1e;
}
</style>

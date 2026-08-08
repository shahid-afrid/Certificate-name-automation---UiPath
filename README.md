# Certificate Name Automation - UiPath

An attended UiPath automation that creates personalised certificates in bulk. It reads participant details from an Excel or CSV file, prints each participant's name onto a certificate template, and then saves or emails the finished certificates.

## Highlights

- Bulk certificate creation from Excel (`.xlsx`, `.xls`) or CSV data
- Custom name position, font family, size, and colour
- PNG and PDF output options
- Local-folder or Gmail delivery
- Built-in email templates: Congratulations, Achievement, and Completion
- Duplicate detection to avoid regenerating existing certificates
- Progress and error logging for every participant

## Technologies used

| Technology | Purpose |
| --- | --- |
| UiPath Studio | Builds and runs the automation workflow |
| C# Invoke Code | Reads participant files, draws names, creates PDFs, and sends email |
| System.Drawing | Renders participant names on certificate images |
| Excel / CSV | Stores the participant list |
| Gmail SMTP | Sends completed certificates by email |
| Git and GitHub | Version control and project hosting |

## Prerequisites

Before running the project, make sure you have:

1. **UiPath Studio 2026.0 or later** installed.
2. A Windows computer. The automation uses `System.Drawing` for image processing.
3. A certificate template in PNG, JPG, or JPEG format.
4. A participant Excel/CSV file with `Name` and `Email` columns.
5. A Gmail account and App Password only if you plan to email certificates.

## Participant file format

Create an Excel or CSV file with these column headers:

| Name | Email |
| --- | --- |
| Alex Johnson | alex@example.com |
| Priya Sharma | priya@example.com |

Save the file and keep it ready before starting the automation.

## Setup and run guide

### 1. Download the project

```bash
git clone https://github.com/shahid-afrid/Certificate-name-automation---UiPath.git
```

Alternatively, download the repository as a ZIP file from GitHub and extract it.

### 2. Open the project in UiPath Studio

1. Open **UiPath Studio**.
2. Select **Open a Local Project**.
3. Browse to the downloaded project folder.
4. Open `project.json`.
5. Allow UiPath Studio to restore dependencies if prompted.

### 3. Start the workflow

1. Open `Main.xaml`.
2. Click **Run**.
3. Select your participant Excel/CSV file.
4. Select your certificate template image.

### 4. Configure certificate design

When prompted, enter:

1. **X position** - horizontal location where the name should appear.
2. **Y position** - vertical location where the name should appear.
3. **Font size** - for example, `48`.
4. **Font family** - for example, `Arial`, `Calibri`, `Verdana`, or `Georgia`.
5. **Font colour** - choose Black, White, Red, Blue, Gold, or enter another colour name.
6. **Output format** - choose `PNG` or `PDF`.

Tip: Run the process first with one test participant to adjust the X/Y position and font size.

### 5. Choose delivery mode

Choose one of these options when UiPath asks for the delivery mode:

- **Local** - select an output folder; certificates will be saved there.
- **Email** - each certificate will be sent to the participant's email address.

## Gmail email setup

Gmail requires an **App Password** for this automation. Do not use your normal Gmail password.

### Create a Gmail App Password

1. Turn on **2-Step Verification** for the Gmail account you want to send from.
2. Open [Google App Passwords](https://myaccount.google.com/apppasswords).
3. Sign in to the sender Gmail account if prompted.
4. Enter a name such as `UiPath Certificate Automation` and click **Create**.
5. Copy the 16-character App Password displayed by Google.
6. Keep it secure. Google shows this password only once.

### Use the App Password in UiPath

1. Select **Email** as the delivery mode.
2. Choose an email template, or enter a custom subject and message.
3. Enter the sender Gmail address when requested.
4. Paste the Gmail App Password when UiPath requests it.
5. The automation sends each generated certificate as an attachment to the matching `Email` address in the participant file.

## How the automation works

```text
Participant Excel/CSV
        |
        v
Read Name and Email
        |
        v
Draw Name on Certificate Template
        |
        v
Generate PNG or PDF
        |
        +--> Save to local folder
        |
        +--> Send through Gmail SMTP
```

## Important security notes

- Never put your Gmail App Password directly in `Main.xaml` or any file committed to GitHub.
- Do not commit participant spreadsheets, certificate templates, or generated certificates if they contain personal or private information.
- The App Password is requested only at runtime and is not stored in this repository.
- This repository's `.gitignore` excludes local data, templates, generated files, and UiPath cache folders.

## Project structure

```text
Main.xaml       # Main UiPath workflow
project.json    # UiPath project settings and dependencies
README.md       # Project documentation
```

## License

Add a license that matches how you want others to use this project.

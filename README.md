# Certificate Name Automation — UiPath

An attended UiPath automation that adds participant names to a certificate template in bulk. It reads participant data from an Excel or CSV file, prints each name in a chosen position and style, then saves the finished certificates locally or emails them to participants.

## Features

- Reads participant names and email addresses from Excel (`.xlsx`, `.xls`) or CSV files.
- Adds each name to a PNG, JPG, or JPEG certificate template.
- Supports custom X/Y placement, font family, font size, and font colour.
- Generates certificates as PNG or PDF.
- Avoids regenerating certificates that already exist.
- Delivers certificates either to a local folder or by Gmail.
- Offers ready-made email templates: Congratulations, Achievement, and Completion.
- Logs progress, skipped rows, duplicates, and processing errors.

## Prerequisites

- UiPath Studio 2026.0 or later
- Windows, because the project uses `System.Drawing`
- A certificate template image
- A participant file with `Name` and `Email` columns

For email delivery, use a Gmail App Password. The password is requested at runtime and is not stored in this repository.

## How to run

1. Clone this repository and open `project.json` in UiPath Studio.
2. Restore the project dependencies if UiPath Studio prompts you.
3. Run `Main.xaml`.
4. Select the participant Excel/CSV file and certificate template image.
5. Enter the name position, font settings, output format, and delivery option.
6. If you select **Email**, provide the sender Gmail address and App Password when prompted.
7. Select the output folder when using local delivery.

## Participant file format

| Name | Email |
| --- | --- |
| Alex Johnson | alex@example.com |
| Priya Sharma | priya@example.com |

Use your own participant data. Input spreadsheets, templates, generated certificates, and local UiPath cache files are intentionally excluded from version control.

## Project structure

```text
Main.xaml       # Main UiPath workflow
project.json    # Project settings and dependencies
```

## Security note

Never commit Gmail App Passwords, participant spreadsheets, or generated certificates. This repository's `.gitignore` excludes these files by default.

## License

Add a license that matches how you want others to use this project.

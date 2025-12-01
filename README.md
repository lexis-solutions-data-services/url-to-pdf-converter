# URL to PDF Converter

👋 Welcome to the URL to PDF Converter! This actor converts any web page into a high-quality PDF document and stores it in the Key-Value Store. Perfect for archiving web pages, generating reports, creating printable versions of websites, and automating document conversion workflows.

<p align="center">
  <img src="https://apify-image-uploads-prod.s3.us-east-1.amazonaws.com/DevbkY3adMTBuoECt-actor-tIcWXjaNli9oRrhiK-m81AjwfbbS-Group_61.jpg" alt="URL to PDF Converter" style="height: 60px; margin-right: 15px;" /><a href="https://apify.com/lexis-solutions/url-to-pdf-converter" target="_blank">
    <img src="https://img.shields.io/badge/Try%20it%20on-Apify-0066FF?style=for-the-badge&logo=data:image/svg+xml;base64,PHN2ZyB3aWR0aD0iNDA4IiBoZWlnaHQ9IjQwOCIgdmlld0JveD0iMCAwIDQwOCA0MDgiIGZpbGw9Im5vbmUiIHhtbG5zPSJodHRwOi8vd3d3LnczLm9yZy8yMDAwL3N2ZyI+CjxnIGNsaXAtcGF0aD0idXJsKCNjbGlwMF8zNDFfNDE1NykiPgo8cGF0aCBkPSJNMjE4LjY5NSAxMDRIMzAwLjk3QzMwMi42NDMgMTA0IDMwNCAxMDUuMzU3IDMwNCAxMDcuMDNWMjMyLjc2NkMzMDQgMjM1Ljc3OCAzMDAuMDgzIDIzNi45NDUgMjk4LjQzNCAyMzQuNDI1TDIxNi4xNTkgMTA4LjY5QzIxNC44NDEgMTA2LjY3NCAyMTYuMjg3IDEwNCAyMTguNjk1IDEwNFoiIGZpbGw9IndoaXRlIi8+CjxwYXRoIGQ9Ik0xODkuMzA1IDEwNEgxMDcuMDNDMTA1LjM1NyAxMDQgMTA0IDEwNS4zNTcgMTA0IDEwNy4wM1YyMzIuNzY2QzEwNCAyMzUuNzc4IDEwNy45MTcgMjM2Ljk0NSAxMDkuNTY2IDIzNC40MjVMMTkxLjg0IDEwOC42OUMxOTMuMTU5IDEwNi42NzQgMTkxLjcxMyAxMDQgMTg5LjMwNSAxMDRaIiBmaWxsPSJ3aGl0ZSIvPgo8cGF0aCBkPSJNMjAyLjU5MSAyMDQuNjY4TDEwOS4xMjcgMjk4LjgzNUMxMDcuMjI5IDMwMC43NDcgMTA4LjU4MyAzMDQgMTExLjI3OCAzMDRIMjk2LjhDMjk5LjQ4MyAzMDQgMzAwLjg0MiAzMDAuNzcgMjk4Ljk2NyAyOTguODUyTDIwNi45MDggMjA0LjY4NUMyMDUuNzI2IDIwMy40NzUgMjAzLjc4MiAyMDMuNDY4IDIwMi41OTEgMjA0LjY2OFoiIGZpbGw9IndoaXRlIi8+CjwvZz4KPGRlZnM+CjxjbGlwUGF0aCBpZD0iY2xpcDBfMzQxXzQxNTciPgo8cmVjdCB3aWR0aD0iMjAwIiBoZWlnaHQ9IjIwMCIgZmlsbD0id2hpdGUiIHRyYW5zZm9ybT0idHJhbnNsYXRlKDEwNCAxMDQpIi8+CjwvY2xpcFBhdGg+CjwvZGVmcz4KPC9zdmc+Cg==&logoColor=white" alt="Try it on Apify" style="border-radius: 12px; height: 60px;" />
  </a>
</p>


## Introduction

## 📊 Actor Stats

| Stat | Value |
|------|-------|
| **Version** | `0.0.1` |
| **Last Update** | Dec 1, 2025 |

---



The URL to PDF Converter is a web automation tool that uses Puppeteer to render web pages and convert them into PDF format. It automatically waits for network idle (ensuring all resources are loaded), waits for fonts to load, handles backgrounds properly, and saves each PDF with a sanitized filename based on the page title.


## 💻 Integration Examples

This repository includes example code showing how to integrate the `url-to-pdf-converter` actor into your projects.

You can find example implementations in the [`examples/`](./examples) folder:
- **TypeScript/JavaScript**: See [`examples/typescript/`](./examples/typescript) for a complete TypeScript example
- **Python**: See [`examples/python/`](./examples/python) for a complete Python example

Each example includes:
- Ready-to-use code templates
- Setup instructions
- Documentation links

---


## Use Cases

- **Web Archiving**: Save web pages as PDFs for archival purposes
- **Document Generation**: Convert web reports, invoices, or receipts to PDF format
- **Content Preservation**: Preserve web content in a stable, printable format
- **Automated Reporting**: Generate PDF reports from dynamic web pages
- **Compliance Documentation**: Create PDF records of web pages for legal or compliance purposes
- **Print-Friendly Versions**: Generate print-ready PDFs from web content

## Input 📥

To use this actor, provide the following input fields:

- **startUrls** (array, required): Array of URLs to convert to PDF. Each URL object can include:
    - `url` (string, required): The web page URL to convert
    - `method` (string, optional): HTTP method (GET, POST, etc.). Default: `GET`
    - `headers` (object, optional): Custom HTTP headers to send with the request
    - `userData` (object, optional): Custom user data to associate with the request

- **proxyConfiguration** (object, optional): Apify proxy configuration. Default: Uses Apify Proxy when available

**Important Notes:**

- The actor will wait for network activity to idle before generating the PDF
- PDFs are generated in A4 format with fonts and backgrounds included
- File names are automatically sanitized to comply with Key-Value Store naming requirements (max 256 characters, allowed characters: `a-zA-Z0-9!-_.'()`)

Example input:

```json
{
    "startUrls": [
        {
            "url": "https://example.com/page"
        },
        {
            "url": "https://example.com/report",
            "method": "GET",
            "headers": {
                "Authorization": "Bearer token123"
            },
            "userData": {
                "customId": "report-001"
            }
        }
    ],
    "proxyConfiguration": {
        "useApifyProxy": true
    }
}
```

## Output 📤

The output consists of two parts:

### 1. Key-Value Store

Each PDF is saved in the Key-Value Store with:

- **Key**: Sanitized filename based on page title (e.g., `Page_Title.pdf`)
- **Value**: PDF binary data
- **Content Type**: `application/pdf`

The PDF files can be accessed via the Key-Value Store API or downloaded from the Apify Console.

### 2. Dataset

Each converted URL generates a dataset record with the following structure:

```json
{
    "url": "https://example.com/page",
    "pdfUrl": "https://api.apify.com/v2/key-value-stores/{storeId}/records/Page_Title.pdf"
}
```

The `pdfUrl` provides a direct link to download the PDF file.

## How many URLs can be converted?

The actor can process any number of URLs you provide in the `startUrls` array. Each URL is processed sequentially, with proper waiting for page loads and network activity to ensure high-quality PDFs.

## Why use the URL to PDF Converter?

- ⚡️ **Fast**: Efficient processing with automatic network idle detection
- 🎨 **High Quality**: Generates PDFs with fonts and backgrounds preserved
- 🔧 **Easy to use**: Simply provide URLs - no coding required
- ☑️ **Well-Maintained**: Maintained by the Lexis Solutions team for reliability and updates
- 📄 **Standard Format**: A4 PDF format suitable for printing and sharing
- 🔒 **Safe**: Automatically sanitizes filenames to comply with storage requirements
- 🌐 **Universal**: Works with any public web page that can be accessed via browser

## Technical Details

- **PDF Format**: A4 size
- **Wait Settings**: Waits for network idle (1 second)
- **Font Loading**: Waits for fonts to load before PDF generation
- **Background**: Includes background graphics and colors
- **Browser**: Uses Puppeteer with headless Chrome
- **Filename Sanitization**:
    - Only allows: `a-zA-Z0-9!-_.'()`
    - Maximum length: 256 characters
    - Invalid characters replaced with underscores

## FAQ 💬

- **Can I convert multiple pages at once?**

    Yes, you can provide multiple URLs in the `startUrls` array. Each URL will be converted to a separate PDF.

- **How do I download the PDFs?**

    PDFs can be downloaded from the Key-Value Store in the Apify Console, or accessed via the API using the `pdfUrl` from the dataset output.

- **What if a page requires authentication?**

    You can include authentication headers in the `headers` field of each URL object, or configure cookies if needed.

- **Can I customize the PDF format?**

    Currently, the actor generates A4 format PDFs. For custom formats, you may need to modify the actor code or request custom development.

- **What happens if a page fails to load?**

    The actor will attempt to generate the PDF regardless. If the page doesn't load properly, you may get a PDF of the error page or loading state.

- **Are the PDFs publicly accessible?**

    PDF URLs in the dataset output are publicly accessible if your Key-Value Store is configured for public access. You can control this in your Apify account settings.

## Need other web automation tools?

Explore related actors on Apify:

- [Apify Run Queue](https://apify.com/lexis-solutions/apify-run-queue) - Run a list of actors with retry mechanism to avoid memory limit errors
- [Browser Use Apify](https://apify.com/lexis-solutions/browser-use-apify) - AI-powered browser automation using natural language to interact with websites

---

👀 Need help or want a custom solution?

Lexis Solutions is a certified Apify Partner. We can help you with custom data extraction projects.

Contact us via [Email](mailto:scraping@lexis.solutions) or [LinkedIn](https://www.linkedin.com/company/lexis-solutions)

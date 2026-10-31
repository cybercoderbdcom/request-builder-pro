🚀 Request Builder Pro

Advanced HTTP Traffic Parser, Authentication Flow Analyzer & Automated Request Code Generator

📥 Download Latest Binaries • ✨ Features • 📦 Built-in Templates • 🛠️ Installation • 🏗️ Project Structure

📖 Overview

Request Builder Pro is a cross-platform desktop GUI application designed for security researchers, API developers, and QA engineers. It ingests captured HTTP/HTTPS traffic from industry-standard proxy tools, automatically detects complex authentication flows (JWT, OAuth, CSRF, Session tokens), tests requests through proxy pools, and generates clean, production-ready request code.

✨ Key Features

🔄 1. Multi-Format Traffic Ingestion (parsers/)

Convert captured network requests from virtually any interceptor into a unified request model:

cURL Commands (curl_parser.py): Full support for Bash and Windows CMD cURL flags, headers, cookies, and data payloads.

HAR Captures (har_parser.py & har_analyzer.py): Import Browser DevTools .har archives with automatic static-asset noise filtering.

Burp Suite (burp_parser.py): Parse exported Burp Suite XML items and raw request dumps.

HTTP Debugger Pro (http_debugger_xml_parser.py): Native parsing for HTTP Debugger XML session logs.

Raw HTTP Streams (raw_request_parser.py): Paste raw HTTP/1.1 or HTTP/2 request headers and bodies directly.

🧠 2. Heuristic Auth & Token Detection Engine (utils/)

Automatically analyzes multi-step traffic dumps to isolate authentication mechanisms and response keychecks:

Token & JWT Extraction (jwt_detector.py, token_detector.py, token_request_detector.py): Identifies Bearer tokens, JWTs, OAuth parameters, and dynamic CSRF nonces across sequential requests.

Login & Auth Flow Detection (login_detector.py, request_detector.py): Pinpoints login endpoints, credential fields, and pre-login handshake requests.

Smart Response Classification (success_detector.py, failure_detector.py, response_field_detector.py): Uses a built-in heuristic keyword database (keyword_database.py) to automatically suggest Success and Failure keychecks from server responses.

Intelligent Noise Reduction (request_filter.py): Strips images, fonts, CSS, and telemetry requests from massive HAR files so you only see relevant API calls.

⚡ 3. Live Request Testing, Proxy Engine & Code Generation (core/)

Code Generator & Formatter (code_generator.py, formatter.py): Generates clean, formatted code snippets from parsed or templated HTTP flows.

Multi-Step Request Flow (request_flow.py, request_preview.py): Chain sequential requests (e.g., GET CSRF token $\rightarrow$ POST Login $\rightarrow$ GET Profile) with live request/response previews.

Integrated Proxy Engine (proxy_engine.py, proxy_parser.py, request_tester.py): Test requests directly from the GUI with support for HTTP, HTTPS, SOCKS4, and SOCKS5 proxies (authenticated IP:PORT:USER:PASS or USER:PASS@IP:PORT formats).

📦 23 Built-in Templates

Request Builder Pro ships with 23 pre-configured JSON templates (templates/) managed via core/template_manager.py:

Generic Auth & API Patterns

Platform & Framework Presets

• api_template.json



• apikey_template.json



• bearer_token_template.json



• csrf_login_template.json



• two_step_csrf_template.json



• graphql_template.json



• html_form_login_template.json



• jwt_template.json



• login_template.json



• oauth_template.json



• redirect_login_template.json



• session_template.json



• signup_template.json

• OpenAI API (openai_template.json)



• Discord (discord_template.json)



• Spotify (spotify_template.json)



• Steam (steam_template.json)



• Twitch (twitch_template.json)



• Netflix (netflix_template.json)



• Crunchyroll (crunchyroll_template.json)



• ExpressVPN (expressvpn_template.json)



• Shopify (shopify_template.json)



• WordPress (wordpress_template.json)



• Django (django_template.json)



• PHP Laravel (php_laravel_template.json)

💡 Custom Templates: You can add your own .json templates directly into the templates/ directory and they will be loaded automatically.

📥 Download Pre-Built Releases (No Python Required)

Standalone executables for Windows, Linux, and macOS are automatically built and published on every push via GitHub Actions.

Go to the Latest Releases Page.

Download the archive for your operating system:

🪟 Windows (64-bit): RequestBuilderPro-Windows-x64.zip

🐧 Linux (64-bit): RequestBuilderPro-Linux-x64.tar.gz

🍎 macOS (Universal): RequestBuilderPro-macOS-Universal.zip

Extract the archive and run RequestBuilderPro.exe (Windows) or ./RequestBuilderPro (Linux/macOS).

(Optional) Verify your download integrity using the SHA256SUMS.txt file attached to the release.

🛠️ Installation & Usage (From Source)

Prerequisites

Python 3.10+ (Python 3.11 recommended)

pip package manager

1. Clone the Repository

git clone https://github.com/cybercoderbdcom/request-builder-pro.git
cd request-builder-pro


2. Install Dependencies

pip install -r requirements.txt


3. Run the Application

Cross-Platform (Terminal):

python main_gui.py


Windows Quick Launch:
Double-click Launcher.bat

4. Build Standalone Executable Locally

Windows: Run Build.bat

Manual PyInstaller Command (Windows/Linux/macOS):

pyinstaller --noconfirm --clean --onefile --windowed --name "RequestBuilderPro" --add-data "templates:templates" --add-data "index.html:." main_gui.py


(Note: Use ; instead of : for --add-data on Windows).

🏗️ Project Structure

request-builder-pro/
├── .github/workflows/
│   └── build-and-release.yml      # Automated CI/CD Cross-Platform Build & Release Pipeline
├── core/                          # Core Execution & Synthesis Engine
│   ├── code_generator.py          # Multi-language / config code generator
│   ├── formatter.py               # Payload & header formatting utilities
│   ├── parsing_engine.py          # Unified traffic parser router
│   ├── proxy_engine.py            # Proxy routing & connection handler
│   ├── proxy_parser.py            # Multi-format proxy string parser
│   ├── request_flow.py            # Multi-step sequential request orchestrator
│   ├── request_preview.py         # Real-time HTTP request/response renderer
│   ├── request_tester.py          # Live request sender & verification engine
│   └── template_manager.py        # Template loader with PyInstaller _MEIPASS support
├── parsers/                       # Traffic Format Parsers
│   ├── burp_parser.py             # Burp Suite XML/raw parser
│   ├── curl_parser.py             # cURL command parser
│   ├── har_parser.py              # HTTP Archive (.har) parser
│   ├── http_debugger_xml_parser.py# HTTP Debugger XML parser
│   └── raw_request_parser.py      # Raw HTTP stream parser
├── templates/                     # 23 Pre-Built Auth & Service JSON Templates
│   └── *.json
├── ui/                            # Modular GUI Components
│   ├── capture_panel.py           # Traffic capture & import interface
│   ├── code_viewer.py             # Syntax-highlighted generated code viewer
│   └── text_editor_utils.py       # Editor helpers and search/replace utilities
├── utils/                         # Heuristic Analysis & Token Detection
│   ├── failure_detector.py        # Automated failure keycheck analyzer
│   ├── har_analyzer.py            # Deep HAR flow analyzer
│   ├── jwt_detector.py            # JWT structure & header inspector
│   ├── keyword_database.py        # Auth/keycheck heuristic dictionary
│   ├── login_detector.py          # Login endpoint classifier
│   ├── request_detector.py        # Request type & payload detector
│   ├── request_filter.py          # Static asset & noise filter
│   ├── response_field_detector.py # Dynamic JSON/HTML field extractor
│   ├── success_detector.py        # Automated success keycheck analyzer
│   ├── token_detector.py          # CSRF, Bearer & OAuth token extractor
│   └── token_request_detector.py  # Pre-auth token source request locator
├── index.html                     # Web dashboard / documentation view
├── main_gui.py                    # Main Desktop GUI Entry Point
├── requirements.txt               # Python dependencies
├── Launcher.bat                   # Windows one-click launcher
└── Build.bat                      # Windows PyInstaller build script


🤝 Contributing

Contributions, new parser modules, and additional service templates in templates/ are welcome!

Fork the repository.

Create your feature branch (git checkout -b feature/new-template).

Commit your changes (git commit -m 'Add new template').

Push to the branch (git push origin feature/new-template).

Open a Pull Request.

⚠️ Disclaimer

This tool is developed strictly for educational purposes, authorized security auditing, API debugging, and automated QA testing. Always ensure you have explicit permission before testing or analyzing third-party endpoints.

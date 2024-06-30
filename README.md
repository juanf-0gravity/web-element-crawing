# TRANCE Web Crawler

[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT)
[![Python 3.8+](https://img.shields.io/badge/python-3.8+-blue.svg)](https://www.python.org/downloads/)

TRANCE (TRacking And Navigating Content Elements) is an advanced web crawler designed to detect and interact with interactive elements on web pages. It uses Chrome with browser extensions to analyze web content and build comprehensive datasets of interactive elements for research and analysis.

## Features

- **Interactive Element Detection**: Automatically identifies clickable elements, forms, and other interactive page components
- **Intelligent Form Filling**: Contextually aware form filling with region-specific data (India, USA)
- **Multi-domain Support**: Process multiple domains concurrently
- **MongoDB Integration**: Store crawling results in MongoDB for further analysis
- **Screenshot Capture**: High-quality screenshots of pages and interactions
- **Adaptive Scrolling**: Smart scrolling to reveal all page content
- **Chrome Extension Support**: Uses custom Chrome extensions for enhanced detection

## Installation

### Prerequisites

- Python 3.8 or higher
- Chrome browser
- MongoDB (local or remote)

### Setup

1. Clone the repository:
   ```bash
   git clone https://github.com/yourusername/trance-web-crawler.git
   cd trance-web-crawler
   ```

2. Create and activate a virtual environment:
   ```bash
   python3 -m venv venv
   source venv/bin/activate  # On Windows: venv\Scripts\activate
   ```

3. Install required packages:
   ```bash
   pip install -r requirements.txt
   ```

4. Install Playwright browsers:
   ```bash
   python -m playwright install chrome
   ```

5. Set up environment variables:
   ```bash
   cp src/config/settings_example.py src/config/local_settings.py
   # Edit local_settings.py with your configuration
   ```

## Configuration

The main configuration is located in `src/config/settings.py`. Key configuration options include:

- `DATA_DIR`: Base directory for storing crawl data
- `EXTENSION_PATH`: Path to the Chrome extension
- `BROWSER_SETTINGS`: Browser configuration (viewport size, headless mode, etc.)
- `CONCURRENT_DOMAINS`: Number of domains to process concurrently
- `DOMAIN_MAX_URLS_PER_SESSION`: Maximum URLs to process per domain
- `MONGODB_URI`: MongoDB connection string (use environment variables for production)
- `FORM_DATA_REGION`: Region for form data generation ("india", "global")

**Environment Variables:**
- `MONGODB_URI`: Your MongoDB connection string
- `MONGODB_DB_NAME`: Database name (default: "web_crawler")
- `REDIS_HOST`, `REDIS_PORT`, `REDIS_USERNAME`, `REDIS_PASSWORD`: Redis configuration (optional)

## Usage

### Basic Usage

Run the crawler with default settings:

```bash
python3 main.py
```

### MongoDB Setup

The crawler requires MongoDB for storing URLs and crawl results. Ensure your MongoDB instance is running and accessible. The connection string can be configured in `src/config/settings.py`.

### Custom Form Data

You can customize the form filling behavior by modifying the `FormDataManager` in `src/crawler/form_data_manager.py` or by providing custom profiles.

## Project Structure

```
trance-web-crawler/
├── chrome_extension/      # Chrome extension for element detection
│   ├── background.js      # Extension background script
│   ├── buildDOMTree.js    # DOM analysis and element detection
│   ├── content.js         # Content script injection
│   ├── pageScript.js      # Page-level interaction handling
│   └── manifest.json     # Extension manifest
├── docs/                  # Documentation
├── main.py                # Main entry point
├── requirements.txt       # Python dependencies
├── src/
│   ├── config/            # Configuration files
│   │   ├── settings.py            # Main configuration
│   │   └── settings_example.py    # Configuration template
│   ├── crawler/           # Core crawler logic
│   │   ├── browser_manager.py         # Browser control
│   │   ├── extension_crawler.py       # Extension-based crawler
│   │   └── form_data_manager.py       # Smart form filling
│   ├── storage/           # Storage management
│   │   └── domain_storage_manager.py  # Domain data handling
│   └── utils/             # Utility functions
│       ├── logger.py              # Logging configuration
│       ├── mongodb_queue.py       # MongoDB queue management
│       └── sitemap_parser.py      # Sitemap processing
└── .gitignore            # Git ignore patterns
```

## How It Works

1. The crawler starts by claiming domains from MongoDB
2. For each domain, it processes URLs in batches
3. Each URL is loaded in a Chrome browser with the extension
4. The extension detects interactive elements on the page
5. The crawler interacts with elements based on configured rules
6. Results are stored in MongoDB and the local filesystem
7. New URLs discovered during crawling are added to the queue

## Troubleshooting

### Common Issues

- **MongoDB Connection**: Ensure MongoDB is running and the connection string is correct
- **Chrome Extension**: Check that the extension path is properly configured 
- **Permission Issues**: Ensure the data directory is writable

### Logs

Logs are stored in the `data/logs` directory by default. Check these for debugging information.

## Example Use Cases

- **Web Accessibility Research**: Analyze interactive elements across websites
- **UI/UX Analysis**: Study form patterns and interaction designs
- **Web Development Testing**: Automated interaction testing
- **Academic Research**: Large-scale web interaction studies

## Contributing

We welcome contributions! Please follow these steps:

1. Fork the repository
2. Create a feature branch (`git checkout -b feature/amazing-feature`)
3. Commit your changes (`git commit -m 'Add amazing feature'`)
4. Push to the branch (`git push origin feature/amazing-feature`)
5. Open a Pull Request

### Development Guidelines

- Follow PEP 8 for Python code style
- Add tests for new functionality
- Update documentation for any changes
- Ensure all tests pass before submitting

## License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.

## Acknowledgments

- Built with [Playwright](https://playwright.dev/) for browser automation
- Uses MongoDB for data storage and queuing
- Chrome extension architecture inspired by modern web development practices

## Support

If you encounter any issues or have questions:

1. Check the [Issues](https://github.com/yourusername/trance-web-crawler/issues) page
2. Review the documentation in the `docs/` directory
3. Create a new issue with detailed information about your problem

## Roadmap

- [ ] Support for additional browsers (Firefox, Safari)
- [ ] Enhanced form field detection algorithms
- [ ] Real-time crawling dashboard
- [ ] API endpoints for external integration
- [ ] Machine learning-based element classification 
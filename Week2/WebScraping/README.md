# PlantVillage Scraper

A simple yet powerful Python script to scrape comprehensive plant information, including diseases and pests, from the [PlantVillage](https://plantvillage.psu.edu/) website. The data is saved locally as a structured JSON file, perfect for agricultural data analysis, research, or building a plant care application.

## Features

- **Basic Info**: Scrapes fundamental plant information like description, common uses, and propagation techniques.
- **Disease Catalog**: Extracts detailed data on common plant diseases, categorized by type (Fungal, Viral, Bacterial, etc.).
- **Pest Guide**: Gathers information on various pests, including their scientific names and management strategies.
- **Image Links**: Collects URLs for images related to the plant, its diseases, and pests.
- **Structured Output**: Saves all scraped data into a clean, well-organized JSON file for easy use.

## Requirements

- Python 3.x
- `requests`
- `beautifulsoup4`

You can install the necessary libraries using pip:

```bash
pip install requests bs4
```

## How to Use

1.  **Clone or Download**
    Clone this repository or download the `plantvillagescrapper.py` script to your local machine.

2.  **Install Dependencies**
    Open your terminal or command prompt and run the installation command from the **Requirements** section above.

3.  **Run the Script**
    Navigate to the script's directory and run it from your terminal:
    ```bash
    python plantvillagescrapper.py
    ```

4.  **Enter Plant Name**
    The script will prompt you to enter the name of a plant. Use a common, one-word name for best results.
    ```
    Enter the name of the plant you want to scrape (e.g., watermelon): tomato
    ```

5.  **Get Your Data!**
    After a successful scrape, a new file named `tomato_data_web.json` will be created in the same directory, containing all the scraped information.

## Output JSON Structure

The output is a JSON file with the following structure:

```json
{
  "basic_info": {
    "description": "...",
    "description_images": [...],
    "uses": "...",
    "propagation": {
      "content": "...",
      "images": [...]
    },
    "references": "..."
  },
  "diseases": {
    "Fungal": [
      {
        "name": "...",
        "pathogen": "...",
        "symptoms": "...",
        "management": "...",
        "images": [...]
      }
    ],
    "Viral": [...]
  },
  "pests": {
    "Insects": [...],
    "Mites": [...]
  }
}
```

## Disclaimer

This scraper is dependent on the HTML structure of the PlantVillage website. If the website is updated, the scraper may need to be adjusted to continue working correctly. Please use this script responsibly and respect the website's terms of service. Thank you!



# Delhi AQI Explorer (Streamlit)

An interactive dashboard to analyze Delhi's Air Quality Index (AQI): pollutants, seasonal patterns, and environmental drivers — plus optional NLP on text feedback.

## Features
- Sidebar filters for **months** and **pollutants** (gases).
- Visualizations: **line chart**, **bar chart**, **histogram**, **box plot**, **scatter**, **correlation heatmap**, **pie chart**.
- Optional **NLP** (keywords + sentiment) if a text column (e.g., `remarks`/`comments`) exists.
- Uses **Matplotlib & Seaborn** for all charts.
- Auto-detects date/pollutant columns where possible.

## Expected Columns
- A date column like `Date` / `Datetime` / `Timestamp` (day-first is supported).
- Pollutant columns such as `PM2.5`, `PM10`, `NO2`, `SO2`, `CO`, `O3`, `NH3`, `AQI`.
- Optional: `Station`/`Location` and environmental drivers like `Temperature`, `Humidity`, `WindSpeed`.
- Optional: text columns like `remarks`, `comments`, `feedback` for NLP.

> If your columns have slightly different names, the app attempts to infer them. You can also rename columns in your CSV.

## How to Run in VS Code (Step-by-step)
1. **Create a project folder** (e.g., `delhi-aqi-dashboard`) and place your CSV inside it (e.g., `delhiaqi.csv`).
2. **Open the folder in VS Code**.
3. **Create a virtual environment** (recommended):
   ```bash
   python -m venv .venv
   # Activate
   # Windows:
   .venv\Scripts\activate
   # macOS/Linux:
   source .venv/bin/activate
   ```
4. **Install dependencies**:
   ```bash
   pip install -r requirements.txt
   ```
5. **Run Streamlit**:
   ```bash
   streamlit run streamlit_app.py
   ```
6. Your browser will open at a local URL. Use the **left sidebar** to upload your CSV (or keep it as `delhiaqi.csv` in the same folder). Choose **pollutants** and **months**, then explore the charts.

## Customization
- Open `streamlit_app.py` and modify:
  - The season mapping in `parse_dates()`.
  - WHO thresholds in `who_thresholds()` used for the exceedance **pie chart**.
  - Add/rename environmental driver columns in `driver_cols` list.

## Troubleshooting
- **No date column detected**: Ensure a column named `Date`/`Datetime`/`Timestamp`, or modify `parse_dates()` in the code.
- **NLP errors**: The app auto-downloads NLTK resources when first used. If you're offline, pre-download `stopwords` and `vader_lexicon`.
- **Blank chart**: Check for missing/NaN values. The app coerces non-numeric entries to numbers where possible.

## License
MIT

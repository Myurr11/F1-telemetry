F1-Viz: Interactive Formula 1 Data Visualization App

About

F1-Viz is an interactive web application built to visualize Formula 1 telemetry and lap data. Developed using Dash and Plotly, the app provides Formula 1 enthusiasts, analysts, and fans with easy access to race data without requiring coding skills. It leverages data from the FastF1 Python library to offer engaging visualizations of both race and qualifying sessions.

The app allows users to explore:

Lap Data: Visualizes high-level race information, including lap times, strategies, and delta comparisons between the winner and other drivers. It provides a broad overview of race progression, guiding users to key laps for deeper investigation using telemetry data.

Telemetry Data: Displays detailed insights into speed, gear, throttle, and brake usage. Available for both race and qualifying sessions, telemetry data can be compared across multiple laps, drivers, and sessions. Typical use cases include comparing drivers' fastest laps or analyzing telemetry to investigate potential crashes or performance issues.

Built with Dash and Plotly, the app is hosted on Heroku for easy online access.

Getting Started

To run the app locally:

Clone the repository and navigate to the project folder:

bash
Copy code
git clone https://github.com/yourusername/f1-viz
cd f1-viz
Create and activate a Python 3 virtual environment and install the required packages:

On UNIX:

bash
Copy code
python3 -m venv venv
source venv/bin/activate
pip install -r requirements.txt
On Windows:

Copy code
python3 -m venv venv
venv\Scripts\activate
pip install -r requirements.txt
Once the dependencies are installed, run the app:

Copy code
python app.py
Open the app in your browser at the default localhost address.

Adding or Updating Data

To download, process, and add or update race data, use the add_session_to_site_data function in the ff1_processing.py module. Example usage for the 2023 Australian Grand Prix:

python
Copy code
import ff1_processing
ff1_processing.add_session_to_site_data(2023, "Australian", "Qualifying", "data")
ff1_processing.add_session_to_site_data(2023, "Australian", "Race", "data")
This will fetch the data for both the qualifying and race sessions, process it, and save it in the data folder in a format compatible with the Dash app.

Heroku Hosting Files

The profile and runtime.txt files are specifically for hosting the app on Heroku. They are not needed for local usage.

Data Storage

Initially, the app stores data in pickle files, which works fine for small datasets. For larger, more complex applications, it's recommended to use a database like SQL to manage data more effectively.

Serverside Caching

Since the app handles large datasets, it uses server-side caching to reduce the load time for repeated data access. This is achieved using dash-extensions. Note that the cache is not automatically cleared, and its size must be managed if you deploy the app outside of Heroku's ephemeral file system.

Data Quality

While the app provides accurate data for general analysis, it is not intended for precise calculations. Some data may be interpolated, and some individual data points may occasionally appear unusual. Always verify data quality if using the app for critical analysis.
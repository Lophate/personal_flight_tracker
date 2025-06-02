# Flight Tracker Application

This application allows users to track real-time flight statuses for multiple flights. It provides a graphical user interface (GUI) to add flights by their IATA code and date, view their current status and details, refresh the information on demand, and persist the tracked flights list between sessions.

## Features

* **Track Multiple Flights:** Add several flights to monitor simultaneously.
* **Real-time Status Updates:** Fetch up-to-date flight information (status, departure/arrival times, airports).
* **Persistent Tracking List:** Tracked flights are saved locally and reloaded when the app starts.
* **Add Flights:** Input Flight IATA code and date to add a new flight to the tracking list.
* **Refresh Data:** Manually refresh status for all tracked flights.
* **Delete Flights:** Remove flights from the tracking list.
* **User-Friendly Interface:** GUI built with web technologies for a modern look and feel.

## Technology Stack

* **Backend:** Python
* **GUI:** `pywebview` (uses native webview components to render HTML/CSS/JavaScript)
* **Frontend UI:** HTML, CSS, JavaScript
* **API:** [AviationStack API](https://aviationstack.com/) for flight data.
* **HTTP Requests:** `requests` Python library.
* **Environment Variables:** `python-dotenv` for managing API keys.
* **Data Persistence:** JSON file (`tracked_flights.json`) for storing the flight list.

## Setup Instructions

1. **Clone the Repository (if applicable):**
   If you obtained this as a Git repository, clone it to your local machine.

   ```bash
   # git clone <repository_url>
   # cd <repository_directory>
   ```

2. **Create and Activate a Virtual Environment (Recommended):**

   ```bash
   python3 -m venv venv
   source venv/bin/activate  # On macOS/Linux
   # venv\Scripts\activate   # On Windows
   ```

3. **Install Dependencies:**
   Ensure your virtual environment is activated, then run:

   ```bash
   pip install -r requirements.txt
   ```

4. **Set Up AviationStack API Key:**
   * Sign up for a free API key at [AviationStack](https://aviationstack.com/).
   * Create a file named `.env` in the root directory of the project (e.g., alongside `flight_tracker_app.py`).
   * Add your API key to the `.env` file in the following format:

     ```env
     AVIATIONSTACK_API_KEY=your_actual_api_key_here
     ```

   * **Important:** The free tier of AviationStack has limitations, such as primarily supporting current-day flight lookups. Queries for specific past or future dates might result in errors or limited data.

## How to Use the Application

1. **Run the Application:**
   With your virtual environment activated and the `.env` file configured, run:

   ```bash
   python3 flight_tracker_app.py
   ```

   A window titled "Flight Tracker" will open.

2. **Adding a Flight:**
   * Enter the **Flight IATA code** (e.g., `UA2457`, `LH100`) in the "Flight IATA" field.
   * Click the "Add Flight" button.
   * The flight will be added to the table with a "Pending..." status, and then its details will be fetched.

3. **Viewing Flight Information:**
   Tracked flights are displayed in a table with columns for:
   * Flight IATA
   * Date (as entered)
   * Status (e.g., Scheduled, Departed, Landed, API Error)
   * Departure Airport
   * Arrival Airport
   * Scheduled Departure Time
   * Actual Departure Time
   * Scheduled Arrival Time
   * Actual Arrival Time

4. **Refreshing Flight Statuses:**
   * Click the "Refresh All Statuses" button to fetch the latest information for all tracked flights from the API.

5. **Deleting a Flight:**
   * Click the "Delete" button for the flight you wish to remove.
   * A confirmation dialog will appear. Click "OK" to confirm.
   * The flight will be removed from the table and from the `tracked_flights.json` persistence file.

6. **Data Persistence:**
   * The list of flights you are tracking is automatically saved to `tracked_flights.json`.
   * When you close and reopen the application, your previously tracked flights will be reloaded and displayed.

## Notes

* If the API key is missing or invalid, the application will print an error to the console and may not function correctly.
* API responses and data accuracy depend on AviationStack.

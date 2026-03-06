# Satellite Orbit Animator

Interactive 3D satellite-orbit visualization built with **Streamlit**, **Plotly**, and **Skyfield**.  
This app propagates a set of sample satellites from **TLE (Two-Line Element) data** and renders:

- A 3D Earth sphere
- Each satellite’s orbit track
- An animated marker showing each satellite’s position over time (Play/Pause)

## Demo / What it does

- Computes satellite positions (in km) using **Skyfield** `EarthSatellite(...).at(times).position.km`
- Generates orbit lines for each satellite across the simulated time range
- Animates satellite positions frame-by-frame in a Plotly 3D scene
- Displays everything in a Streamlit web app

## Included satellites (sample TLEs)

The app currently includes TLEs (hardcoded in `satellite_app.py`) for several objects such as:

- ISS (ZARYA)
- HST
- STARLINK-1008
- IRIDIUM 33
- NOAA 1
- and others

## Time range simulated

The current code simulates **August 2024**, for **31 days**, sampled **hourly** (24 samples/day).  
You can change this in `satellite_app.py` by editing the `days`, `hours`, and the `ts.utc(...)` call.

## Requirements

Dependencies are listed in `requirements.txt`:

- streamlit
- plotly
- numpy
- skyfield

## Installation

```bash
git clone https://github.com/nihira91/Satellite_orbit_animator.git
cd Satellite_orbit_animator

python -m venv .venv
# macOS/Linux:
source .venv/bin/activate
# Windows (PowerShell):
# .\.venv\Scripts\Activate.ps1

pip install -r requirements.txt
```

## Run the app

```bash
streamlit run satellite_app.py
```

Then open the local URL Streamlit prints (typically `http://localhost:8501`).

## Project structure

- `satellite_app.py` — Streamlit app + orbit propagation + Plotly animation
- `requirements.txt` — Python dependencies
- `README.md` — project documentation

## Customization ideas

- Replace hardcoded TLEs with user input (text area / file upload)
- Add a satellite selector / toggles to show/hide specific orbits
- Increase/decrease animation speed (`frame.duration`) or time resolution
- Change the scene axis ranges or add Earth texture / night lights

## Notes / limitations

- TLEs become stale over time; for accurate current positions you should update TLEs from a live source.
- The visualization is in an Earth-centered coordinate frame (km) and is intended for educational/visual purposes.

## License

Add a license file if you plan to distribute or reuse this project (e.g., MIT, Apache-2.0).

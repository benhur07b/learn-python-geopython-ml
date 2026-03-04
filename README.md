# GeoPython & ML Exercises

A collection of notebooks and exercises covering Google Earth Engine, GeoPython, Geospatial ML, Geospatial Deep Learning, and GeoAI.

---

## Local setup w/ uv

### Prerequisites

- [uv](https://docs.astral.sh/uv/getting-started/installation/)

### Install and run

1. Clone the repository and navigate to the project directory.

2. Install dependencies:

   ```bash
   uv sync
   ```

3. Launch JupyterLab:

   ```bash
   uv run jupyter lab
   ```

---

## Google Colab

You can run these notebooks directly in [Google Colab](https://colab.research.google.com/) without any local setup.

### Open in Colab

Click the badge below to browse and open notebooks from this repository in Google Colab:

[![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/benhur07b/learn-python-geopython-ml/blob/main/)

Or navigate directly to:

```
https://colab.research.google.com/github/benhur07b/learn-python-geopython-ml
```

### Install dependencies

Once a notebook is open in Colab, install the required dependencies by running the following at the top of the notebook:

Most dependencies should already be available in Colab. If not, you can install packages individually as needed:

```sh
!pip install <package-name>
```

### Notes

- Colab provides free GPU/TPU access, which is useful for deep learning notebooks. Change your Colab runtime as needed.
- Files created during a session are temporary and will be lost when the session ends unless saved to Google Drive.

---

## Issues with Google Earth Engine Authentication

Before you can use Google Earth Engine (GEE), you need to:
1. Have or create a Google account.
2. Request access to GEE (non-commercial or commercial).
3. Enable the Earth Engine API for your Google Cloud project.

### Requesting a non-commercial use account

1. Go to [https://earthengine.google.com/noncommercial/](https://earthengine.google.com/noncommercial/).
2. Click **Get started for free** and sign in with your Google account.
3. Fill out the registration form. Select the appropriate non-commercial use type (e.g., research, education).
4. Submit the form and wait for an approval email from Google. This may take a few minutes to a few days.

> **Note:** Non-commercial use is free but intended for research, education, and non-profit applications. For commercial use, see [https://earthengine.google.com/commercial/](https://earthengine.google.com/commercial/).

### Enabling the Google Earth Engine API

Once your account is approved, you need to enable the Earth Engine API for a Google Cloud project:

1. Go to the [Google Cloud Console](https://console.cloud.google.com/).
2. Create a new project or select an existing one.
3. In the search bar, search for **Earth Engine API** and select it.
4. Click **Enable**.
5. Make note of your **Project ID** — you will need it when initializing GEE in your notebooks.

### Authenticating in notebooks

After enabling the API, authenticate and initialize GEE in your notebook:

```python
import ee

# Run once to authenticate (opens a browser window for OAuth)
ee.Authenticate()

# Initialize with your Cloud project
ee.Initialize(project="your-project-id")
```

- `ee.Authenticate()` only needs to be run once per environment. It stores credentials locally.
- `ee.Initialize()` must be called at the start of every session.

> **Tip:** In Google Colab, use `ee.Authenticate()` with `auth_mode="notebook"` if the default browser flow does not work:
> ```python
> ee.Authenticate(auth_mode="notebook")
> ```
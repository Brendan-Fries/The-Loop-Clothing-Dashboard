# The Loop Clothing Dashboard
Dashboard of Analytics from The Loop GWU Clothing & Textile Exchange
![R](https://img.shields.io/badge/Made%20with-R-blue.svg) ![Quarto](https://img.shields.io/badge/Quarto-Shinylive-orange.svg) ![Status](https://img.shields.io/badge/Status-Active-brightgreen.svg)

An interactive, serverless dashboard designed to visualize operations data for **The Loop**, a clothing exchange program. This application tracks inventory distribution, visitor demographics, and donation trends to help stakeholders understand community engagement and resource flow.

## Live Demo
*[https://brendan-fries.github.io/The-Loop-Clothing-Dashboard/The_Loop_Dashboard.html]*

---

## Purpose
The goal of this dashboard is to provide real-time (or periodic) insights into the clothing exchange's impact. It answers key operational questions:
* **Who is visiting?** (Demographic breakdown)
* **What is being taken?** (Inventory outflow by category)
* **Are visitors donating back?** (Sustainability and circular economy metrics)
* **How does activity change over time?** (Temporal trends)

## Key Features

### 1. Serverless Architecture (Shinylive)
Unlike traditional Shiny apps that require an R server (like Shinyapps.io), this dashboard compiles entirely to **WebAssembly**. It runs directly in the user's web browser, making it incredibly fast, secure, and free to host on GitHub Pages.

### 2. Interactive Filtering
* **Demographic Segmentation:** Users can filter all visualizations by specific visitor demographics (e.g., "Student," "Faculty," "Community Member") using the interactive sidebar.
* **Dynamic Data Processing:** All metrics re-calculate instantly based on the active filters.

### 3. Visualizations
* **Activity Timeline:** A line graph showing the volume of items distributed over time, with weekly axis scaling for clarity.
* **Donation Habits:** A pie chart visualizing the proportion of visitors who brought donations vs. those who did not.
* **Inventory Distribution:** A bar chart ranking the most popular clothing categories (e.g., Tops, Pants, Accessories) with exact counts displayed.

---

## Tech Stack

* **Language:** R
* **Framework:** [Shiny](https://shiny.rstudio.com/) (UI/Server logic)
* **Publishing:** [Quarto](https://quarto.org/) with [Shinylive](https://github.com/posit-dev/r-shinylive) extension.
* **Libraries:**
    * `bslib`: For the modern "Darkly" Bootstrap theme.
    * `dplyr` & `tidyr`: For data cleaning and transformation.
    * `lubridate`: For robust date parsing.

---

## Project Structure
* ├── The_Loop_Dashboard.qmd          # Main Quarto document containing the R code and UI
* ├── loop-data-ldw-2026.csv      # Source data file (must be in root directory)
* ├── README.md          # Project documentation
* ├── _site/             # Generated HTML files (created after rendering)

## Data Requirements
The dashboard expects a CSV file named `loop-data.csv` with the following columns:

| Column Name | Description |
| :--- | :--- |
| **Visit Date** | Dates in formats like `MM/DD/YYYY` or `YYYY-MM-DD`. |
| **Demographics** | Categorical data for filtering (e.g., "Student", "Staff"). |
| **Donation Status** | "Yes", "No", or "Donated at blue bin". |
| **Item Columns** | Counts for specific items: `Tops`, `Pants`, `Shoes`, `Accessories`, etc. |

---

## How to Run Locally

1.  **Clone the Repository**
    ```bash
    git clone <https://github.com/Brendan-Fries/The-Loop-Clothing-Dashboard>
    ```

2.  **Install Required R Packages**
    Open RStudio and run:
    ```r
    install.packages(c("shiny", "bslib", "dplyr", "tidyr", "lubridate"))
    ```

3.  **Install Quarto Extension**
    In your terminal/command prompt within the project folder:
    ```bash
    quarto add quarto-ext/shinylive
    ```

4.  **Render the App**
    Open `index.qmd` in RStudio and click the **Render** button, or run:
    ```bash
    quarto preview index.qmd
    ```

---

## Deployment (GitHub Pages)

To deploy this serverless app to the web:

1.  Render the project locally to create the `_site` (or `docs`) folder.
2.  Push the changes to GitHub.
3.  Go to **Settings > Pages** in your GitHub repository.
4.  Set the **Source** to `GitHub Actions` or deploy from the `docs` folder branch.

---

## Author
**Brendan Fries**
* *Affiliation:* George Washington University Milken Institute School of Public Health
* *Role:* PhD Candidate, Global Public Health Sciences
* *Contact:* bfries@gwu.edu

---

*This project is an entry into the George Washington University 2026 Data Visualization Competition.*

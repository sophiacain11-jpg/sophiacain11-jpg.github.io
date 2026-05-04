# Unemployment Dashboard

"Exploring Unemployment Effects on New Yorkers," sets out to investigate how unemployment shapes the lives of New York City residents across multiple lifestyle indicators. The initial research questions focused on job postings, education levels, and the relationship between unemployment and crime, but the project evolved significantly as data limitations were encountered. Vehicle collision data proved too weak a proxy for crime, and job posting records were unreliable due to deletions as listings were updated. This prompted a pivot toward more meaningful variables: eviction rates and physical health outcomes, sourced from FRED and NYC Open Data respectively. The revised research questions centered on housing instability, health outcomes, and how policymakers could use this data to design better social benefit programs for unemployed New Yorkers.

![dashboard_sc](/Users/sophiacain/Desktop/main/sophiacain11-jpg.github.io/Screenshot 2026-05-03 at 11.24.37 PM.png)

The project relied heavily on pandas for data manipulation and cleaning, including filtering time-series unemployment data by borough and year, handling inconsistent date formats, and merging datasets from disparate sources into unified dataframes ready for analysis. NumPy supported the underlying numerical operations, particularly when computing estimated unemployment figures and normalizing variables across boroughs for cleaner visual comparisons. Data was pulled from public APIs including NYC Open Data and FRED, transformed and structured using pandas, then pushed into Google BigQuery tables.
On the Streamlit side, the app queried BigQuery at runtime to populate its dashboard and individual analysis pages, but this introduced significant performance challenges. To address slow load times, incremental loading strategies were implemented: checking the maximum existing date in a BigQuery table before appending only new records, rather than re-fetching entire datasets on every run. Streamlit's built-in caching decorators were also applied to expensive query functions, ensuring data was only re-fetched when necessary rather than on every user interaction. The richness of interactive geographic visualizations were carefully balanced, built with PyDeck's HexagonLayer for borough-level mapping, against the performance cost they introduced, ultimately cleaning up unused code and streamlining rendering logic to keep page load times reasonable.

![dashboard_sc_2](/Users/sophiacain/Desktop/main/sophiacain11-jpg.github.io/Screenshot 2026-05-03 at 11.24.57 PM.png)

The final product included a multi-page Streamlit application backed by Google BigQuery, featuring an interactive dashboard that displayed key unemployment metrics alongside borough-level maps and trend analyses. Along the way, challenges around data filtering, caching performance, and the inherent difficulty of quantifying abstract concepts like health and housing stability were navigated. Looking ahead, several enhancements worth pursuing: more accurate unemployment metrics, healthcare access data such as uninsured rates, and a richer historical employment record for New York City have been identified for further analysis and integration.

The Streamlit dashboard can be found at this link:
https://bouncy-banana.streamlit.app/

The Github, housing all the project’s code can be found at this link:
https://github.com/advanced-computing/bouncy-banana/tree/main

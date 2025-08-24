# **Netflix Content Analysis: A Data Exploration Project**

## Project Overview

This project performs an in-depth Exploratory Data Analysis (EDA) on Netflix's film and TV show catalog. The primary goal is to clean, explore, and visualize the dataset to uncover insights into the content available on Netflix, including trends in content type, ratings, release years, and geographical production.

The analysis is conducted using a Python-based Jupyter Notebook, leveraging powerful data science libraries like Pandas, NumPy, Seaborn, and Matplotlib.

## **Dataset**

* **Source:** The analysis uses the netflix\_titles.csv dataset.  
* **Size:** 8,807 titles (rows) and 12 features (columns).  
* **Original Features:**
  * show\_id: Unique ID for each title.  
  * type: Whether the title is a "Movie" or "TV Show".  
  * title: Name of the title.  
  * director: Name of the director.  
  * cast: List of actors featured in the title.  
  * country: Country/countries where the title was produced.  
  * date\_added: The date the title was added to Netflix.  
  * release\_year: The year the title was originally released.  
  * rating: The content's rating (e.g., TV-MA, PG-13, R).  
  * duration: Length of the movie (in minutes) or number of seasons (for TV shows).  
  * listed\_in: Genres and categories describing the title.  
  * description: A brief synopsis of the plot.

## **Methodology & Data Cleaning**

The notebook follows a structured data cleaning and preparation process to ensure data quality before analysis.

1. ### **Initial Setup and Inspection**

   * Libraries such as pandas, numpy, seaborn, and matplotlib are imported for data manipulation and visualization.
   * The dataset is loaded from a CSV file stored on Google Drive.
   * An initial inspection reveals the dataset's shape **(8807, 12\)** and a preview of the first few rows.

2. ### **Data Cleaning Steps**

   The raw dataset contained several data quality issues that were addressed:

    * **Date Conversion:** The date\_added column was converted from a string to a proper datetime object to enable time-based analysis.  
    * **Whitespace Stripping:** Leading/trailing whitespace was removed from all string columns to ensure consistency.  
    * **Duplicate Removal:** Any duplicate entries were dropped from the dataset.  
    * **Handling Missing Values:**

    * Rows with critical missing values in rating, duration, or date\_added were dropped entirely (reducing the dataset to **8,702 entries**).  
    * Missing values in director, country, and cast were filled with the string "Unknown" to preserve the rows for other analyses. This is a practical approach as these columns had a very high volume of missing data.  
    * **Final Missing Values Count:** After cleaning, the dataset had **zero missing values**.

#### **Summary of Missing Values Handled:**

| Column | Original Missing Values | Action Taken |
| :---- | :---- | :---- |
| director | 2,634 | Filled with "Unknown" |
| country | 831 | Filled with "Unknown" |
| cast | 825 | Filled with "Unknown" |
| date\_added | 98 | Dropped rows |
| rating | 4 | Dropped rows |
| duration | 3 | Dropped rows |

## **Exploratory Data Analysis (EDA) & Key Findings**

The cleaned dataset was then analyzed to extract meaningful insights.

1. ### **Content Type Distribution (Movies vs. TV Shows)**

![Content Type Distribution (Movies vs. TV Shows)][images/picture1.jpg]

**Finding:** Netflix's catalog is heavily skewed towards **Movies**.  
**Visualization:** A count plot was used to visualize the disparity.  
**Insight:** This suggests Netflix's initial and potentially core strategy was built around a vast movie library, though TV show production and acquisition have grown significantly in recent years.

2. ### **Content Rating Analysis**

![Content Rating Analysis][images/picture2.jpg]

**Finding:** The majority of content on Netflix is geared towards **mature audiences**.  
**Visualization:** A count plot was generated, ordered by the frequency of each rating.  
**Key Insights:**

* **TV-MA** (Mature Audience) is the most common rating by a significant margin. This indicates a strong focus on adult-oriented content (dramas, crime series, adult comedies).  
* **TV-14** and **PG-13** are the next most common ratings, targeting teenagers and adults.  
* Content for children (PG, G) and family-friendly content (TV-PG, TV-G) is less prevalent.

3. ### **Distribution of Genres**

![Distribution of Genres][images/picture3.jpg]

**Findings**
  * "International Movies" is the most common genre by a very large margin.  
  * Dramas, Comedies, and Documentaries form the next largest groups.  
  * The top 15 includes a mix of movie and TV genres, showing a diverse but adult-skewed catalog.

**Visualization**
  * A horizontal bar chart effectively shows the top 15 genres.  
  * Genres are sorted from most to least frequent, making comparisons easy.  
  * The length of each bar directly represents the count of titles in that genre.

**Key Insights**
  * **Global First:** The platform's identity is heavily defined by its vast international content library.  
  * **Adult Audience:** The dominance of genres like Dramas and Comedies, paired with earlier rating data, confirms a primary focus on adult viewers.  
  * **Diverse Strategy:** The catalog successfully blends broad appeal genres with niche categories to serve a wide range of tastes.

**Conclusion:** The genre distribution reveals a platform with a distinctly **global and adult-oriented identity**. Its strategy is built on a massive foundation of international content, supplemented by strong offerings in standard popular genres and a respectable selection for niche audiences and families. This is not a niche service but one competing on the breadth and diversity of its global catalog.

4. ### **Distribution of release years**

![Distribution of release years][images/picture4.jpg]

**Findings:** 
  The vast majority of content was released after the year 2000, with a dramatic and exponential increase beginning around the 2010s. Very little content exists from before 1980\.

**Visualization:** 
  A histogram shows the count of titles by their release year. It uses a wide bin range (e.g., 20 years) to group the data, making the overall trend clear.

**Key Insight:** 
  The platform's library is overwhelmingly modern, focusing on contemporary content from the last two decades, with a massive surge in recent years.

**Conclusion**: 
This is not an archive of classic films but a modern, actively updated content library. The distribution suggests a strategic focus on acquiring and producing new content to attract a contemporary audience, aligning with the trends of a streaming service that prioritizes recent releases and original programming.

5. ### **Distribution of titles added over time (yearly)**

![Distribution of titles added over time (yearly)][images/picture5.jpg]

**Findings:** 
  The number of new titles added each year was low and stable until approximately 2014\. After 2014, there was a period of massive, rapid growth that peaked around 2018-2019, followed by a significant decline.

**Visualization:** 
  A line chart showing the number of titles added per year. The x-axis is the year, and the y-axis is the volume of new content, clearly illustrating the major growth trend and subsequent drop.

**Key Insight:** 
  The platform experienced a major expansion phase in its mid-life, aggressively building its library before drastically scaling back its new acquisitions or productions in recent years.

**Conclusion:** 
This trajectory is classic of a maturing streaming service: an **initial slow build, followed by explosive growth to capture market share, and finally a strategic shift towards optimization and profitability** rather than pure volume, likely focusing on higher-quality or more targeted content.

6. ### **Distribution of titles added over time (monthly)**

![Distribution of titles added over time (monthly)][images/picture6.jpg]

**Findings**:   
  The number of new titles added varies significantly by month. There are clear peaks (likely in certain months like January, May, or December) and troughs throughout the year, suggesting a seasonal release pattern.

**Visualization**:   
  A line chart showing the number of titles added per month across multiple years. The repeating up-and-down pattern reveals consistent seasonal trends.

**Key Insight:**   
  New content is not released uniformly. The platform follows a seasonal strategy, strategically bulking up its library during specific times of the year to capitalize on viewer engagement (e.g., holiday seasons, summer breaks).

**Conclusion**:   
Content releases are highly planned. The platform times its new additions to align with periods of high demand, using a "content calendar" to maximize subscriber retention and attract new viewers with major releases during key moments.

7. ### **Distribution of Most Frequent Movie Genres**

![Distribution of Most Frequent Movie Genres][images/picture7.jpg]

**Findings:**   
  "International Movies" is the dominant movie genre by a very large margin. It is followed by broad categories like Dramas, Comedies, and Documentaries. More niche genres like "Music & Musicals" round out the bottom of the top 10\.

**Visualization:**   
  A horizontal bar chart displaying the top 10 movie genres, sorted by count. The length of each bar visually represents the volume of titles in each category.

**Key Insight:**   
  The movie library has a strong global focus and is built on a foundation of universal, broad-appeal genres (Dramas, Comedies), with a healthy selection of niche categories to cater to specific tastes.

**Conclusion:**   
The platform's movie strategy prioritizes diversity and international appeal, using a core of popular genres to attract a wide audience while offering specialized content to satisfy dedicated fanbases. This is not a niche movie service but a general one with a distinct global identity.

8. ### **Distribution of Most Frequent TV Shows Genres**

![Distribution of Most Frequent TV Shows Genres][images/picture8.jpg]

**Findings:**   
"International TV Shows" is the most common TV genre. It is followed by mainstream categories like "TV Dramas" and "TV Comedies." The list includes a mix of reality, kids, and niche genres like "Anime Series."

**Visualization:**   
  A horizontal bar chart ranking the top 10 TV show genres by count. The bars decrease in length, showing the drop-off in volume after the top few genres.

**Key Insight:**   
  Similar to its movie strategy, the platform's TV library has a strong international emphasis. It balances popular broad genres with targeted content for specific audiences (e.g., kids, anime fans).

**Conclusion:**   
The TV catalog is designed for global and diverse viewer preferences, combining widely appealing dramas and comedies with specialized genres to serve niche interests and demographics.

9. ### **Distribution of Frequent Directors on Netflix**

![Distribution of Frequent Directors on Netflix][images/picture9.jpg]

**Findings:**   
  The most frequent directors have a relatively low number of titles (around 20 or fewer). The list features a mix of international names (e.g., Rajiv Chilaka, Cathy Garcia-Molina) and well-known Hollywood directors (Martin Scorsese).

**Visualization**:   
  A horizontal bar chart showing the top 10 directors by the number of titles they have on the platform. The counts are low and tightly grouped, indicating no single director dominates the library.

**Key Insight:**   
  The platform's content is not reliant on a few prolific directors. Instead, it features a diverse and international roster of creators, from prolific makers of smaller content (e.g., children's shows) to acclaimed award-winning filmmakers.

**Conclusion**  
Netflix's strategy is one of volume and variety, not auteur-driven curation. It partners with a wide range of directors worldwide to create a massive and diverse library that caters to every segment of its global audience, from mass-market entertainment to prestige cinema.

10. ### **Distribution of Frequent Actors on Netflix**

![Distribution of Frequent Actors on Netflix][images/picture10.jpg]

**Findings:**
  The most frequent actors appear in a moderate number of titles (around 30 or fewer). The list is dominated by actors from Indian cinema (e.g., Anupam Kher, Shah Rukh Khan) and Japanese voice actors (e.g., Takahiro Sakurai).

**Visualization:** 
  A horizontal bar chart ranking the top 10 actors by their number of titles on the platform. The counts are relatively low and close together.

**Key Insight:** 
  The platform's most common actors are not Hollywood A-listers but **prolific stars from international film industries**, particularly India and Japan. This highlights a content strategy focused on volume production in specific regional markets.

**Conclusion:** 
The actor data reinforces that the platform's core strategy is **global and volume-driven**. By featuring actors who are extremely prolific in their home industries (especially Bollywood and Anime), the platform efficiently builds a deep catalog for key international audiences.

11. ### **Country based analysis**

1. #### **The top 10 countries producing Netflix content**

   ![Top 10 countries producing Netflix content][images/picture11.jpg]

   **Findings**: 
    The United States produces the vast majority of content, with over 3000 titles. India is a distant second, followed by the United Kingdom, Canada, and France. The output of other countries is significantly lower.

   **Visualization:** 
    A horizontal bar chart ranking the top 10 content-producing countries. The bar for the United States is dramatically longer than all others, visually highlighting its dominance.

   **Key Insight:** 
    The platform's content production is heavily US-centric, but it maintains a strong international footprint with strategic investments in major markets like India and the UK.

   **Conclusion:** 
   The strategy is a hybrid: a massive core of US-driven content for global appeal, supplemented by targeted productions in key international markets to capture local audiences and provide regional diversity. This balances global scale with local relevance.

2. #### **A world map visualization of content production**

![A world map visualization of content production][images/picture12.jpg]

  **Findings**:
    The United States is the dominant country of production by a very large margin. A "long tail" of many other countries (e.g., India, UK, Japan, South Korea) contributes the remaining content, each with significantly smaller counts.

  **Visualization:**
    A horizontal bar chart showing the number of titles produced by each country. The bar for the United States is vastly longer than all others, visually establishing its dominance.

  **Key Insight:** 
    While the platform has a global audience and a diverse international library, its content production is heavily centralized in the United States. The strategy is a hybrid: a massive core of US-produced content supplemented by key regional productions for major international markets.

  **Conclusion:** 
    The platform operates a "Glocalization" strategy: producing a high volume of content in its primary market (the US) for global export, while also investing in local original productions in other countries to win market share and provide authentic regional content. This allows it to be both a global powerhouse and a local player.

## **Conclusion**

This initial phase of the Netflix analysis successfully transformed a raw, messy dataset into a clean, structured, and analysis-ready resource. The key findings reveal a content library dominated by **Movies** and geared towards **mature audiences (TV-MA)**.

The cleaning process was crucial, addressing significant missing data in key columns like director and country without drastically reducing the dataset's size for other analyses.

## **Technologies Used**

* **Python:** Core programming language.  
* **Jupyter Notebook:** Interactive development environment.  
* **Pandas:** Data manipulation and analysis.  
* **NumPy:** Numerical computations.  
* **Matplotlib:** Basic plotting and visualization.  
* **Seaborn:** Advanced statistical data visualization.

**To run this analysis yourself**, ensure you have the required libraries installed (pip install pandas numpy seaborn matplotlib) and upload the netflix\_titles.csv dataset to your environment.

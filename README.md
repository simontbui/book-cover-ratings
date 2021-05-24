# Classification of eBook Ratings by Cover
## Problem & Motivations
I publish eBooks on Amazon's Kindle store. One of the struggles in the business is to identify what covers to use when publishing a story. The current decision-making approach is based off of intuition and subjective preference. Typically, hypothesis testing and other approaches would be used to more systematically, and effectively, decide between design choices; examples of such are common in advertisement/visual selections (e.g. A/B testing). However, due to the mechanics and scale of the business, such an approach would not be practical. 
  
This project is an attempt to evaluate the relationship, if any, between eBook covers and their ratings. The problem is addressed by collecting eBook images and their ratings (4* or 5*). If a relationship does exist, this allows us to explore potential classification models that can predict how well a cover would perform. Ultimately, this would allow for a more methodical approach for cover selections.

Intuitively, we might expect that no relationship exists between an eBook cover and their ratings. This is based off of the assumption that a product's rating is based on the content (i.e. the actual story, plot, writing, etc.), and not the cover. If this assumption is true, then we would expect that a binary classification model's precision to be 50%, which signifies that the prediction performs no better than a random guess. Considering the scale of such businesses can often exceed over $100k in annual revenue, I'd like to verify and challenge this intuition.

## Data
Using the ProxyCrawl API, over 6000 eBook images and their product ratings were webscraped from the historical romance genre in Amazon's Kindle store. The code for the webscraping can be found in scrape_img-ratings.ipynb and the resulting dataset can be viewed from ebook_info.csv.

## Process
To account for variability in image sizes, only the most common image size was retained from the dataset. As a result, over 1800 images were retained. Because Amazon's product ratings are in increments of 0.1 (e.g. 4.1, 4.2, 4.3, etc.), all product ratings were rounded to their nearest integer (4 or 5). This allows for a simplification of the task while still allowing the investigation of which covers are better (i.e. a binary classification). 

The final dataframe is then used to build classification models using SVM and logistic regression using Python's Sci-kit Learn.

## Results


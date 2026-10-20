# Forage · British Airways Data Science

My work from the [British Airways Data Science job simulation](https://www.theforage.com/simulations/british-airways/data-science-yqoz) on Forage, completed in November 2022.

The simulation has two modules. The first asked me to collect customer reviews of the airline from Skytrax, clean them and pull out insights for a one-slide summary. The second asked for a model that predicts whether a customer completes a holiday booking, with a one-slide summary of what drives it.

## What is in this repo

| Path | What it is |
| --- | --- |
| `1-review-insights/scraper.ipynb` | A threaded scraper built on requests and BeautifulSoup. It reads the Skytrax A to Z list of airlines and saves each airline's category scores and latest reviews. |
| `1-review-insights/exploratory.ipynb` | Cleaning and analysis of the British Airways reviews, including sentiment labels from a pretrained Hugging Face model. |
| `1-review-insights/summary.md` | The text and charts from my one-slide summary. |
| `1-review-insights/*.png` | The charts I exported for that slide. |
| `2-booking-prediction/booking-model.ipynb` | Data preparation, two OLS baselines, a neural network classifier (scikit-learn `MLPClassifier`) and a check of how each feature correlates with a completed booking. |
| `2-booking-prediction/summary.md` | The text and chart from my one-slide summary. |
| `requirements.txt` | The Python packages the notebooks import. |
| `data/README.md` | Which files go in `data/` and where they come from. |

## What I found

The scraper collected reviews for 485 airlines, which is about 89% of the airlines Skytrax lists. Of the 1,200 British Airways reviews, the sentiment model labelled 72.2% negative and 27.8% positive. The A320 and the Boeing 777 were the most reviewed aircraft, and most reviewers were solo leisure travellers flying Economy.

For the booking data (50,000 records), the neural network scored 0.850 on the training set and 0.852 on the test set. No single feature had a strong relationship with completing a booking. Wanting extra baggage and wanting a preferred seat had the strongest positive correlation, and flight duration had the strongest negative one.

## Looking back

Only about 15% of the bookings in the data were completed, so a model that always predicts "no booking" would also score about 0.85. My classifier's score is therefore close to that baseline. I now put the class balance and a naive baseline next to any score I report.

## Running the notebooks

1. Install the packages with `pip install -r requirements.txt`.
2. Create `data/airline_reviews/` and run `1-review-insights/scraper.ipynb` to collect the reviews. Please check the Skytrax terms of use first and keep the request rate low. `exploratory.ipynb` then reads `data/airline_reviews/british-airways.csv`.
3. The booking data belongs to the programme. `booking-model.ipynb` downloads it from the link the programme used in 2022. If that link stops working, enrol in the simulation on Forage, download `customer_booking.csv` and save it in `data/`.

Outputs that printed rows of the booking data or the text of individual reviews have been cleared from the saved notebooks. Charts, model summaries and scores are kept.

## What is not in this repo

I left out everything that was not my own work. That covers the Forage task briefs, the booking data, the scraped Skytrax reviews, the starter notebook and example answers that came with the programme, and the programme's PowerPoint template, which carries the British Airways logo. The text and charts from my two slides are kept in the `summary.md` files instead.

## Licence

My code and writing in this repo are under the [MIT licence](LICENSE). The licence does not cover the booking data, the Skytrax reviews, the Forage briefs or any British Airways material, and none of those are included here.

# SPOTIFY CHARTS API (Unofficial)
A fully-fledged installable python package for extracting **top 200** and **viral 50** charts off of [spotifycharts.com](http://spotifycharts.com)

## INSPIRATION
This was built to fill the gap left when Spotify deprecated their official Spotify charts API. It arose as a needed crawler for the Spotify data analysis and machine learning project done [here](bit.ly/incitefuldata)

## INSTALLATION
```bash
pip install fycharts
```


## SAMPLE USAGE
Say you want to extract top 200 daily charts for all time, all regions
```python
from fycharts import SpotifyCharts 

api = SpotifyCharts.SpotifyCharts()
api.top200Daily(output_file = 'top_200_daily.csv')
```
Run your program. 
```bash
python myCrawler.py
```
Watch the terminal for helpful information.

## FUNCTIONS AND PARAMETERS
Four functions, for all data you need are required:
1. top200Weekly
2. top200Daily
3. viral50Weekly
4. viral50Daily

All four functions take the following parameters:
#### Compulsory
1. output_file - CSV file to dump the data. 

#### Optional
1. start - Start date of range of interest as string YYYY-MM-DD
2. end - End date of range of interest as string YYYY-MM-DD

Refer to 'PASSING DATES AS PARAMETERS' below for important information on this.

3. region - Region of interest, as a country abbreviation code. 'global' is also valid

Refer to 'SUPPORTED COUNTRY CODES SO FAR' below for important information of this.

If not included, data is extracted for all dates, all regions

## DATA RETURNED
The data extracted from spotifycharts.com is written into a CSV file with the following fields:
1. position - The song's position during that week or day
2. track name - Name of the song
3. artist - Name of artist
4. region - Region of the chart as a code
5. date - Date or range of dates of chart
6. id - Spotify track id
7. streams - Number of streams for that week or day. **Only applicable to top 200 charts**

## SUPPORTED COUNTRY CODES SO FAR
'global', 'ad', 'ar', 'at', 'au', 'be', 'bg', 'bo', 'br', 'ca', 'ch', 'cl', 'co', 'cr', 'cy', 'cz', 'de', 'dk', 'do', 'ec', 'ee', 'es', 'fi', 'fr', 'gb', 'gr', 'gt', 'hk', 'hn', 'hu', 'id', 'ie', 'il', 'is', 'it', 'jp', 'lt', 'lu', 'lv', 'mc', 'mt', 'mx','my', 'ni', 'nl', 'no', 'nz', 'pa', 'pe', 'ph', 'pl', 'pt', 'py', 'ro', 'se', 'sg', 'sk', 'sv', 'th', 'tr', 'tw', 'us', 'uy', 'vn'

## PASSING DATES AS PARAMETERS
For V1.0.0 dates need to be passed following some strict guidelines.
1. Data goes as far back as 2017-01-05 for viral 50 weekly, 2016-12-22 for top 200 weekly, and 2017-01-01 for all daily.
2. Due to (1) above, when passing the start date esp. for weekly data, the date must be i + (7 days * n) where i: First date defined in (1) above, and n: number of weeks.
If the date isn't valid, you shall be notified with a list of valid dates
3. The API returns data up to and excluding the date passed in the 'end' parameter

## STUFF YOU SHOULD KNOW
When extracting data for a range of dates, in loop, the crawler sleeps every iteration for a random number of seconds between 0 and the index of the date. Dig into the code to change this!!!


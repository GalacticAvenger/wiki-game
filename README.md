# Overview

The Wiki Racer Web Crawler is designed to navigate from one Wikipedia URL to another by utilizing a breadth-first search algorithm. It scrapes for Wikipedia links on each page it visits until it reaches the destination page.

# How It Works

1. Starting Point
The crawler begins with a specified origin URL. This URL serves as the entry point for the search.

2. Fetching the Page
Using the File_fetcher module, the crawler retrieves the HTML content of the origin page. This is done with a simple command that allows the program to access online or local resources:

'''
dune exec ./bin/wiki_game.exe -- file-fetcher-demo -resource <origin-url>
'''
3. Parsing HTML
Once the page is fetched, the crawler employs the Lambda Soup library to parse the HTML. It identifies key elements, such as links to other Wikipedia articles, by examining the document structure.


4. Extracting Links
The crawler specifically looks for links that lead to other Wikipedia articles. The wikipedia_namespace module helps filter out irrelevant links (such as those pointing to external sites or non-article namespaces). The extraction process involves:

Identifying anchor (<a>) tags.
Checking the href attribute for links that match the Wikipedia format.
Storing valid links for further exploration.

5. Breadth-First Search Algorithm
With the links extracted, the crawler implements a breadth-first search (BFS) strategy. This involves:

Maintaining a queue of URLs to visit, starting with the origin URL.

Tracking visited URLs to avoid cycles.

Iteratively fetching and parsing each page linked in the current URL until the destination page is found or all options are exhausted.

6. Navigating to the Destination
As the crawler processes each URL:

It fetches the page content.

Parses the HTML to extract links.

Checks if any of the newly found links match the destination URL.

If a match is found, the crawler records the path taken from the origin to the destination.

7. Output
Upon reaching the destination page, the crawler outputs the full path taken, displaying each Wikipedia article visited along the way. The result provides a clear route through Wikipedia’s interconnected articles.

Example Command
To initiate the crawling process, use the following command:

'''
dune exec ./bin/wiki_game.exe -- wiki-game find-path -origin <origin-url> -destination <destination-url> -local-with-root resources/
'''
Example Output
The output will display the path traversed, such as:

Copy code
Cat - Wikipedia
Carnivore - Wikipedia
Caniformia - Wikipedia
Dog - Wikipedia
Conclusion

The Wiki Racer Web Crawler efficiently navigates the vast landscape of Wikipedia articles by leveraging web scraping and a breadth-first search algorithm. This allows users to explore connections between topics and understand how knowledge is interlinked across the platform. Happy crawling!

# nanoscrape

A simple manga scraper.

Made by Zirconium (@FortiethAtom4 on Github)

# HOW TO USE THIS SCRAPER

1. Get a link to the chapter from any of the sites nanoscrape recognizes.
Full list of recognized domains:
- ciao.shogakukan.co.jp
- tonarinoyj.jp
- shonenjumpplus.com
- pocket.shonenmagazine.com

This list will continue to increase; nanoscrape.js is in continuous development with the goal to be able to recognize and scrape from as many manga sites as possible.

- Example test links:
    - from Ciao: https://ciao.shogakukan.co.jp/comics/title/00511/episode/9255 (NekoMeru Chapter 5)
    - from Young Jump: https://tonarinoyj.jp/episode/4856001361151760115 (Love Agency Chapter 1)
    - from Shounen Young Jump: https://shonenjumpplus.com/episode/3269754496567812827 (Kokoro no Program Chapter 1)

2. Get Node.js.
    - link to download: https://nodejs.org/en/download

3. Open a terminal and navigate to this folder. Any terminal, such as Command Prompt or Git Bash, will do.

4. Type the following into the command line: `npm install`. This will install everything the scraper needs to work.

5. Type the following into the command line: `node nanoscrape.js [URL]`, where `[URL]` is the chapter URL.

6. The scraper will get your images and write them to the "images" folder. This may take some time, depending
on your Internet connection and your computer's resources.

# USAGE

Command: `node nanoscrape.js [URL] [(optional) timeout] [(optional headless)] [(optional) path]`

# OPTIONS

**timeout**
The command waits for the network to be idle before beginning scraping. The default wait time is 1000 milliseconds. You can change this value by adding a number (in milliseconds) to the end of the command. For example, the following will wait for 5000 milliseconds of network idle time instead of 1000 before scraping:

`node nanoscrape.js [URL] 5000`

This is done to ensure all images have loaded before scraping begins. If your computer is slow or your internet connection is choppy, consider using a higher timeout time to compensate. To avoid causing bugs during scraping (i.e. missing pages), I highly recommend not using values lower than 1000 milliseconds.

**headless**
By default, the scraper uses a headless browser to get images; that is, it does not visually render the browser while it operates. You can tell the scraper to render the page it is using by adding "false" at the end of the command line.
*NOTE:* You must also enter a timeout value when using this command.

Example:
`node nanoscrape.js [URL] 1000 false`

**path**
By default, the scraper will automatically generate a name for the image folder. You can override this by adding in a custom name for your folder(s) on the command line. The folder generates from the directory nanoscrape.js is in. Subfolders are permitted, e.g. "folder-1/folder-2". The images will be saved in folder-2, within folder-1. 
*NOTE:* You must also enter a timeout value and a headless value (true or false) when using this command.

Examples:
`node nanoscrape.js [URL] 1000 true path/to/my/folder`
`note nanoscrape.js [URL] 1000 true "folder name with spaces"`

# ENJOY

----

# PATCH NOTES

5/5/2024 - Optimized scrape strategy and changed loop condition to check page URL, finally killing the extra-image bug.
WARNING: There is a bug with automated logins which causes the scraper to time out after the page loads. Do not use automated logins for pocket.shonenmagazine.com for the time being.

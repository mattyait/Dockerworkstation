Installing on Mac.
1. brew update
2. brew install hugo
3. Create a hugo skeleton
	>> hugo new site path/to/site
	>> cd path/to/site
4. Create some content
	>> hugo new about.md
5. To install hugoscroll theme
	>> git clone https://github.com/SenjinDarashiva/hugoscroll themes/hugoscroll		
6. Start the watching your folder
	>> hugo --buildDrafts --theme="hugoscroll" --watch server
7. Open localhost:1313


Running on Docker

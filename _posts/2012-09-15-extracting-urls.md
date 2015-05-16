---
layout: post
Title: Extracting URLs using lxml
---
I am extracting URLs that lead to test cricketers' profiles from [here](http://stats.espncricinfo.com/ci/engine/stats/index.html?class=1;template=results;type=batting).

![](http://db.tt/t29KeL98)

Now that's about 2682 players, 50 players a page for 54 pages!! I'd like to get details like Date of birth, place of birth, Major teams, batting styles, bowling styles etc.

![](http://db.tt/95aLT1EV)

This is how the html looks like. We are going to be extracting the links (circled in red).

![](http://db.tt/U6UTd6W6)

Here's the piece of code which does the job!

		import lxml.html
		base_url = 'http://stats.espncricinfo.com/ci/engine/stats/index.html?class=1;template=results;type=batting'
		content = lxml.html.parse(base_url)
		links = content.xpath('//tr[@class="data1"]/td[1]/a/@href')
		player_links = [player for player in links]
		print player_links


- First import the lxml library

		import lxml.html


- Store the root url in a variable

		base_url = 'http://stats.espncricinfo.com/ci/engine/stats/index.html?class=1;template=results;type=batting'

- Parse the url

		content = lxml.html.parse(base_url)

- Extract the link using xpath
	
		links = content.xpath('//tr[@class="data1"]/td[1]/a/@href')

- Store the extracted links in a list

		player_links = [player for player in links]

Wait a minute!!! The above piece of code would give us the links for the first 50 players in the first page. But we've got 53 pages more to go!!! Lets do something about that.

		import lxml.html
		base_url = 'http://stats.espncricinfo.com/ci/engine/stats/index.html?class=1;template=results;type=batting'
		url_part1 = 'http://stats.espncricinfo.com/ci/engine/stats/index.html?class=1;'
		url_part2 = 'page='
		url_part3 = 'template=results;type=batting'
		url_list = ['http://stats.espncricinfo.com/ci/engine/stats/index.html?class=1;template=results;type=batting']
		for i in range(2,55):
			url_next = url_part1 + url_part2 + str(i) + ';' + url_part3
			url_list.append(url_next)
		players = [ ]
		for page in url_list:
			content = lxml.html.parse(page)
			links = content.xpath('//tr[@class="data1"]/td[1]/a/@href')
			player_links = [player for player in links]
			players.extend(player_links)
		print players


Now that we've captured the player profile URLs for 2682 players, lets see what else we could do with them in the forthcoming posts.	

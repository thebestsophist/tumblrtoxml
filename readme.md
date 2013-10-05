# Tumblr to xml

This takes a Tumblr archive generated with [tumblr-rb](https://github.com/mwunsch/tumblr), and turns it into a single XML file. 

## Requirements

- Rubygems
- [tumblr-rb](https://github.com/mwunsch/tumblr)


## Instructions
1. If you have not done so, install `tumblr-rb` with the command `gem install tumblr-rb`

1. Clone this repo:

1. Enter the directory and download your tumblr archive to `_posts`

		`$ TUMBLRHOST=yourbloghere.tumblr.com tumblr backup _posts/`

1. Enter the `_posts` directory and rename the archived posts to something jekyll will like:

		`$ find *.txt -exec bash -c 'mv "$0" "2013-10-05-${0%\.txt}.markdown"' {} \;`

You can replace the date `2013-10-05` with any date you prefer, jekyll requires it, but it is not used in the generated XML file. I prefer to use the date of import.

1. Mass replace `id: ` with `tumblrid: `

[Need good command for this that only matches the `id:` in the yaml front matter.]

1. Return to your jekyll root and build the xml file:

		`jekyll build`
		
Jekyll will still build individual pages for your posts, you can ignore those, the important file is `index.xml` which will contain your entire 


## Notes
Since Tumblr is terrible at generating clean XHTML, post contents are shoved into a `<![CDATA[]>`. You may need to clean up the data a little more if you plan on using it to generate your sites.
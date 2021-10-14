#I was tired of manually changing all my headers, footers, and head code.

There are options - yes. You have PHP, but that is server side and with my website being hosted on GitHub for now, that's not an option. Javascript and html_include is probably the best option out there for this, and it is probably better than this solution. That said, Javascript adds weight and reliability issues that I'm not sure I want to deal with.

So I wrote this little script to automate the update of headers, footers, and heads. It is dead simple, and relies on a human marking each of their pages with HTML comments. The thing is, it's simple to understand, all the processing is done locally with the developer (me), so mistakes are caught immediately and before they are published, and all my webpages remain plain HTML and CSS for *maximum speed*.

## How It Works

Wrap your head, headers, and footers with HTML comments. These *MUST* be on their own lines in the code. Your elements can go in their respective files in the templates directory, they are .txt, and if you want them to be active HTML just change the extensions in the Python code. All the pages you want to include should be listed, separated by `newlines` in the _includes.txt file.

#### Headers Look Like This:
\<!--HEADER BEGINS HERE-->
*HEADER CONTENT*
\<!--HEADER ENDS HERE-->

#### Footers Look Like This:
\<!--FOOTER BEGINS HERE-->
*FOOTER CONTENT*
\<!--FOOTER ENDS HERE-->

#### Heads Look Like This:
\<!--HEAD BEGINS HERE-->
*HEAD CONTENT*
\<!--HEAD ENDS HERE-->

The Python script will read the file, remove the lines with the old elements, replace them with the new elements, wipe the old code, and write the new code. Yes it's a little scary that the file is wiped and then written to. There are some safety checks to make sure you have valid tags and so forth, and only when eveything is in place does the truncation and write happen, so it should be pretty safe. I could have the script create a backup that it cleans up in case of some erro, but honestly, I'm not worried enough about that edge case, and Git exists.

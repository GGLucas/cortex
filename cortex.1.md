# Cortex
## NAME
cortex - reddit browser and monitor

## SYNOPSIS
cortex SUBREDDIT

## DESCRIPTION
Browse through reddit article lists from the cli.

## KEYBINDINGS
* `q`:
  Quit cortex and go back to the terminal.

* `r`:
  Update/Refresh the cortex listing from reddit.

* `m`:
  Toggle between full and minimal display mode.

* `x`:
  Toggle whether to display only new posts.

* `o`, `Return`:
  Open the currently selected link in the browser.

* `c`:
  Open the comments page for the currently selected link
    in the browser.

* `t`:
  Open both the currently selected link and the comments
    page in the browser.

* `i`:
  Open the reddit messages inbox in the browser.

* `h`:
  Jump to the frontpage listing.

* `s`:
  Prompt for a subreddit to display the listing for.

* `f`:
  Jump to the subreddit the currently selected article is
  in. Alternatively, when already viewing a subreddit,
  jump back to the frontpage.

* `z`:
  Mark the currently selected link as read.

* `l`:
  Mark all articles in the list as read.

* `/`:
  Prompt for searching reddit.

* `Up`, `k`:
  Move one entry up the list.

* `Down`, `j`:
  Move one entry down the list.

* `0`, `g`, `Home`:
  Go to the first entry in the list.

* `$`, `G`, `End`:
  Go to the last entry in the list.

* `Control+B`, `Page Up`:
  Move one page up the list.

* `Control+F`, `Page Down`:
  Move one page down the list.

## CONFIGURATION
See config.example for an example configuration file to put in ~/.cortex/config,
the following options are available:

### frontpage=http://reddit.com/.json
    Frontpage json url, substitute your personal one here if you want
    cortex to display your own subreddit subscriptions.

### inbox=
    Unread messages json url, put your personal one here if you want
    cortex to display your unread message count.

### sort=-read
    Field to sort the entries by. A "-" in front of the field name
    indicates a reverse sort order.

    Not specifying a sort option will leave the ordering to reddit
    (this usually means you will see the same order in cortex as
    you would on your frontpage).

    Some fields that can be sorted by:
        created: Article creation time
        title: Article title alphabetically
        score: Article total score
        read: Whether the article is marked read or not

### title-format= Cortex -- Reddit/{title}: {total} articles, {new} new
    Format used in the application title bar.
    Note: In python 2.5, use %(VAR)s formatting.

    Available variables:
        {title}: Title of the current subreddit or "Frontpage".
        {total}: Total amount of articles in the listing.
        {new}: Amount of unread articles in the listing.

### entry-format-minimal= {title} %> {subreddit:<13} | {num_comments:4}
### entry-format-full= {title} %n  [{score:4}] {read} {nsfw} %> {domain:30}
###                   {subreddit:<13}   {num_comments:4} comments
    Formats used for entries in the list in minimal and full mode 
    respectively.
    Note: In python 2.5, use %(VAR)s formatting.

        Available variables:
            {title}: Article title.
            {subreddit}: Article subreddit.
            {num_comments}: Amount of comments the article has.
            {score}: Article score
            {ups}: Article total upvotes
            {downs}: Article total downvotes
            {domain}: Article domain
            {author}: Article submitter/author

            {read}: "[New]" if the article is new, empty otherwise.
            {nsfw}: "NSFW" if the article in not safe for work, empty otherwise.

    You can use %> to indicate that the rest of the line should be aligned
    to the right of the screen.

    In the full entry format, you can use one "%n" to indicate the separation
    between the top and bottom lines in the listing.

### seen-size=500
    Amount of articles to save seen/read status for.

### browser-command=
    Command to invoke the webbrowser. The {0} will be replaced by the url
    to open. (Use %s in python 2.5)

    If left empty, cortex will try to autodetect the default browser for
    the system.

### browser-background=1
    Whether the browser command should be backgrounded. Set to 0 to
    wait for the browser to finish before continuing cortex execution.

    This is needed when using console browsers like lynx or w3m so they do
    not get executed in the background.

### update-interval=10
    Amount of minutes between automatic updates/refreshes.

### minimal=0
    Whether to start cortex in minimal mode. Same as pressing 'm'.

### hideold=0
    Whether to hide already displayed or seen links when starting cortex.
    Same as pressing 'x'.

## COLOR CONFIGURATION
You can also change the colors used in the configuration, the colors
available are: black, red, green, yellow, blue, magenta, cyan, white, default
and their respective bright- versions.

Colors are specified in (foreground, background) pairs, the available
items to set the colors for are:

### title=brightyellow,blue
    The titlebar on top of the interface.

### normal=white,black
    Normal text.

### entry=white,black
    The main part of an entry.

### entry-data=yellow,black
    The right/data part of an entry.

### entry-selected=brightyellow,magenta
    The main part of a selected entry.

### entry-data-selected=brightyellow,magenta
    The right/data part of a selected entry.

### entry-bottom=green,black
    The main part of the bottom line of an entry in full mode.

### entry-bottom-selected=brightyellow,magenta
    The main part of the bottom line of a selected entry
    in full mode.

### entry-bottom-data=yellow,black
    The right/data part of the bottom line of an entry in full mode.

### entry-bottom-data-selected=brightyellow,magenta
    The right/data part of the bottom line of a selected entry in full 
    mode.

### messages=brightgreen,blue
    The unread messages count in the top right of the application.


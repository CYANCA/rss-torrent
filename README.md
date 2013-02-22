# rss-torrent

The rss-torrent script is a small php script for automatically downloading torrent files from an RSS feed that an rTorrent or transmission client can pick up. It is intended to be used entirely from a command line interface or crond.

This has been tested and works on a netgear stora but should work anywhere that has php

The script stores the RSS feed list and other configuration in the actual file itself

1. Clone the script and place it in an executable directory. It should already be chmod'ed to be executable, but if it isn't, go ahead and do that.
2. Open the `rss-torrent` script in a text editor
3. Update the location of the `TORRENT_DIRECTORY` define. This should be the same directory that rTorrent watches for new .torrent files.
4. Update the location of the `MATCH_CRITERIA` define. This should be a regex to match new .torrent files.
5. Update the runTests function to ensure that your regex matches things you want but does not match things you don't
6. Add a feed using the script itself: `rss-torrent add "http://www.site.com/path/to/example/feed.rss"`
7. If you re-open the `rss-torrent` script, you'll see the URL of the feed at the bottom! Neat, huh? To remove a feed, just delete it's line and save the file.
8. You can optionally execute the `rss-torrent` script manually, or set it up on a cron to run discretely. On each execution, it will fetch the feed, see what .torrent files have already been downloaded, and then download the new ones. Of course, this means you shouldn't delete the .torrent files after they're done downloading.

I have the following line in my crontab that runs the script every 20mins and outputs details of the last run to a file:
*/20 * * * * root /home/0common/rss-torrent.php>/home/0common/rss.log

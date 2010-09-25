# rss-torrent

The rss-torrent script is an easy to use, small, and efficient script for automatically downloading torrent files
from an RSS feed that an rTorrent client can pick up. It is intended to be used entirely from a command line interface
(similar to rTorrent).

One neat thing about rss-torrent is that it stores the RSS feed list in the actual file itself! Using the script, you
can easily add another RSS feed and it will be automatically picked up the next time to script is executed. Let's see
how that works.

1. Clone the script and place it in an executable directory. It should already be chmod'ed to be executable, but if it isn't, go ahead and do that.
2. Open the `rss-torrent` script in a text editor and updated the location of the `TORRENT_DIRECTORY` define. This should be the same directory that rTorrent watches for new .torrent files.
3. Add a feed using the script itself: `rss-torrent add "http://www.site.com/path/to/example/feed.rss"`
4. If you re-open the `rss-torrent` script, you'll see the URL of the feed at the bottom! Neat, huh? To remove a feed, just delete it's line and save the file.
5. You can optionally execute the `rss-torrent` script manually, or set it up on a cron to run discretely. On each execution, it will fetch the feed, see what .torrent files have already been downloaded, and then download the new ones. Of course, this means you shouldn't delete the .torrent files after they're done downloading.
6. If you set it up on a cron, make it no more often than ever 6 hours to be nice to the RSS torrent hosts.

That's it!

-Vic Cherubini <vmc@leftnode.com>
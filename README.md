https://github.com/Atemu/bookwalker-dl

# Running
In shell, run 
```shell
nix-shell shell.nix
bash bw-dl.bash <cid>
```

This tool helps you make private copies of bookwalker books that are available publicly under the `viewer-trial` subdomain.  
It might work for other books too but that's not my goal here and probably doesn't work (it might with a few cookies and tweaks though).

The tool takes a cid (the UUID-like strings in the bookwalker URLs) and an optional download location as arguments and downloads every page of the book in order.
The default download directory is `./$cid/` and you can make it relative to a different path by setting the second argument.

In this directory the tool creates:

* `cid`: A text file containing the cid
* `name`: A text file containing actual name of the book
* `metadata.json`: Metadata about chapters and pages (mostly used internally but also contains things like page- and chapter names)
* `chapters/`: A directory with all chapters as sub-directories that contain the individual pages' images
* `pages/`: A directory with sequentially named symlinks to the chapters' pages
* `isManga`: A file that contains 1 if the downloaded book is a manga and 0 if it isn't
* `progress`: A file that contains the already downloaded pages while the script is running. If it still exists after the script finished running, something went wrong!

Dependencies are listed in `shell.nix`, they should be pretty clear even if you don't use Nix.

Manga are supported but their images will be jumbled. The jumbling is probably reversible but this program can't do that yet.

# License

This project is licensed under the GPLv2 or, at your choice, any later version released by the Free Software Foundation.
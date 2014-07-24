#Apaxy

Demo: [adamwhitcroft.com/apaxy](http://adamwhitcroft.com/apaxy/)

Apaxy is a customisable theme built to enhance the experience of browsing web directories. It uses the `mod_autoindex` Apache module—and some CSS—to override the default style of a directory listing.

This is a fork of the [https://github.com/AdamWhitcroft/Apaxy](original Apaxy) made for the [CERN](http://cern.ch) [ALICE](http://alice.cern.ch/) Release Validation.

##Features

Apaxy may be basic, but it gives you a great deal of creative freedom when styling your directory.

* Style your directory listing with CSS.
* Make it pop with Javascript or jQuery.
* Add welcome messages, download instructions or copyright notices.
* Add custom mime type icons (requires editing the `.htaccess` file)

_Sadly, visual style is all you can work with. It's not possible to alter the generated table structure of the listing directory with Apaxy._

##Installation

Apaxy requires an Apache(2.0.23+) enabled HTTP server.

To install it:

    cd /var/www
    mkdir apaxy
    cd apaxy
    git clone https://github.com/dberzano/Apaxy.git .

_In this case the theme directory will end up in `/var/www/apaxy/apaxy/theme`._

Now, copy the sample configuration file to your Apache configuration directory:

    cp /var/www/apaxy/apaxy/apaxy.conf /etc/httpd/conf.d/apaxy.conf

_The destination directory changes depending on your Linux distribution and Apache installation._

Edit the destination file; go to the end, and change all occurrences of `/var/www/apaxy/apaxy/theme` to the appropriate directory. If you have unpacked under `/var/www/`, there is no need to change anything.

You then have to enable indexing explicitly for the directories you want to list. Edit or create a configuration file in `/etc/httpd/conf.d` that contains:

    <Directory /path/on/local/filesystem>
      Option +Indexes
    </Directory>

##Apaxy themes

If you'd like to alter the default Apaxy theme, look in the `/theme` folder and you'll find the following files:

* `header.html`
* `footer.html`
* `style.css`

Edit these as you would any other HTML or CSS file.

Adding your own icons is a little more involved. You'll need to edit the main Apaxy `.htaccess` file. Look for the following as an example:

    AddIcon /apaxy/theme/icons/gif.png .gif

The above rule will assign an icon named `gif.png` from the directory `/apaxy/theme/icons/` to any file with the `.gif` extension.

_Remember that the directory `/apaxy` is a "virtual directory": Apache will map it to your local filesystem's directory according to the appropriate `Alias` directive._

##Mime Types

The default Apaxy theme `/themes/apaxy` has icons in place for the following mime types:

    .aif .aif .asf .asx .avi .bin .c .css .csv .dmg .doc .docm .docx .dot .dotm .eps .flv .gif 
    .htm .html .ico .iff .jar .jpeg .jpg .js .json .log .m3u .m4a .md .mid .mov .mp3 .mp4 .mpa 
    .mpg .msg .mwa .odt .pages .pdf .pkg .png .ps .psd .ra .rar .rb .rm .rss .rtf .shtml 
    .sql .srt .swf .tex .tiff .txt .vob .wav .wmv .wpd .wps .xhtml .xlam .xlr .xls .xlsm .xlsx 
    .xltm .xltx .xml .zip


##Credits

This is a fork of the original [Apaxy](https://github.com/AdamWhitcroft/Apaxy): all credits go to Adam Whitchcroft ([GitHub](https://github.com/AdamWhitcroft), [Twitter](https://twitter.com/adamwhitcroft)).

Apaxy owes it's existence to the amazing [h5ai](http://larsjung.de/h5ai/) by [Lars Jung](https://twitter.com/lrsjng). Had I not seen this, I would never have looked into making my own (probably way less useful) version.

[Faenza Icons](http://tiheum.deviantart.com/art/Faenza-Icons-173323228) are used in the `apaxy` theme.

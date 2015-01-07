###This is a fork/collection of binaries to use *CSS3 Font Converter* Created by Zoltan Hawryluk. 

It is a tool that makes 'web fonts' for use on your internet webpages. The end result is sort of like the output of Font Squirrel, but not nearly as easy to use.

It supports .ttf or .otf fonts.

You can read the original page about this [here](http://www.useragentman.com/blog/2011/02/20/converting-font-face-fonts-quickly-in-any-os/).

You can view their github repo [here](https://github.com/zoltan-dulac/css3FontConverter).

While Zoltan has done some great work, trying to find all of the various dependencies and components is a big pain.

Hopefully what I've done here will be of use to someone. The binaries were assembled on an Arch Linux i386 32-bit build, and hopefully will work for others.

Using this big collection of stuff isn't exactly straight forward but there are two important documents that you might need.

I've included the original 'readme' from Zoltan as well as the 'readme' from an awesome subsetting script for fontforge created by, Mikhail Kashkin, Raph Levien, and Dave Crossland of Google.

---------

Dependencies that you'll need to install:

fontforge (compiled to run python scripts, and its depends)
ttfautohint (and its depends - only if you want your fonts hinted.. many fonts will look like crap without this)
python2.x (and whatever it depends on)

---------

###Here is the way I go about using this:

1. Place the font(s) I want to convert in the fonts folder.

2. Subset the font(s) using commands like these two:

For one font:

	coolperson@linux:fontconv/:$ python2.7 ./bin/subset.py --subset=latin --script --strip_names --new ./fonts/LibreCaslon.ttf ./fontoutput/LibreCaslon-subset.ttf

For many fonts go inside of the fonts folder and run something like this:

	coolperson@linux:fonts/:$ for font in `ls -1 *ttf | cut -d. -f1`; do /usr/bin/python2.7 ../bin/subset.py --subset=latin --script --strip_names $font.ttf ../fontoutput/$font.ttf; done; 

3. Edit the convertFonts.sh file in the bin/ folder to point to the correct path for all of the binaries and scripts (including wherever you've installed fontforge).

4. Use CSS3FontConverter to convert the fonts by navigating to the fontoutput folder, then run the script make a bunch of web fonts to use in your web pages:

	coolperson@linux:fontoutput/:$ ../bin/convertFonts.sh --autohint *.ttf

Running #4 will produced all kinda of files in your fontoutput folder, including a CSS stylesheet that you can use to include these fonts in your website. Keep the 'hinted' files and copy those to your site, these are the ones that have been subsetted and converted.

-----------

###Notes: 

* You'll see all kinds of crazy text scroll past when you use these scripts. So long as the fonts that come out seem to appear correctly when you open them in your OS, all should be good.

* You'll need fontforge to have been compiled with python scripting. The default fontforge that installed from the arch packages worked for me. 

* Also, fontforge requires python 2.x to use with scripting, 3.x will not work.

* I have no idea what the file called "old" is that gets generated upon using the CSS3FontConverter script. You can safely ignore it (I think).

* The original css3FontConverter contains a folder of about 80megabytes worth of opensource fonts to mess about with, along with example output from the tools. It is included here as well.

---------
I've done little more than collect/build some binaries and figure out how to use this all (which was a bit of work).

the credit goes to those who actually made it.... you can visit the blog/original repo for more info on the stuff used for licenses and all the relate stuff..

------------

CSS3 @font-face Converter v2.1 by Zoltan Hawryluk (http://www.useragentman.com) More info available at http://useragentman.com/blog/8QtbI


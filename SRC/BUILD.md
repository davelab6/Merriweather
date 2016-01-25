Open all the UFOs in Glyphs v2.3b

File, Export to your Desktop, choose to remove overlaps, autohint, and do not save as TrueType

Make a directory for the release

    mkdir 2016-02-30
    cd 2016-02-30

and copy the built files in

    mkdir OTF;
    mv ~/Desktop/Merriweather-*.otf OTF/;

File, Export to your Desktop, choose to remove overlaps, do not autohint, and save as TrueType

Then hint the fonts with ttfautohint v1.4.1

    mkdir TTF;
    cd TTF;
    mkdir UNHINTED;
    mv ~/Desktop/Merriweather-*.ttf UNHINTED/;
    for i in `ls -1 UNHINTED/*ttf`; do \
      echo $i; ttfautohint -l 6 -r 36 \
      -G 0 -x 10 -H 350 -D latn -f cyrl \
      -w "" -X "" -I \
      $i $i-ta;
    done;
    mv UNHINTED/*-ta . ; 
    rename s/ttf-ta/ttf/g *;

Then fixup the TTX files by hand, correcting the NAME table

    cd ../..;
    ttx -s 2016-02-30/*/*tf;
    mate */*x 

Then recompile

    ttx 2016-02-30/OTF/Merriweather-Black.ttx;
    ttx 2016-02-30/OTF/Merriweather-BlackItalic.ttx;
    ttx 2016-02-30/OTF/Merriweather-Bold.ttx;
    ttx 2016-02-30/OTF/Merriweather-BoldItalic.ttx;
    ttx 2016-02-30/OTF/Merriweather-Italic.ttx;
    ttx 2016-02-30/OTF/Merriweather-Light.ttx;
    ttx 2016-02-30/OTF/Merriweather-LightItalic.ttx;
    ttx 2016-02-30/OTF/Merriweather-Regular.ttx;
    ttx 2016-02-30/TTF/Merriweather-Black.ttx;
    ttx 2016-02-30/TTF/Merriweather-BlackItalic.ttx;
    ttx 2016-02-30/TTF/Merriweather-Bold.ttx;
    ttx 2016-02-30/TTF/Merriweather-BoldItalic.ttx;
    ttx 2016-02-30/TTF/Merriweather-Italic.ttx;
    ttx 2016-02-30/TTF/Merriweather-Light.ttx;
    ttx 2016-02-30/TTF/Merriweather-LightItalic.ttx;
    ttx 2016-02-30/TTF/Merriweather-Regular.ttx;

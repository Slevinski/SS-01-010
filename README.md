# SS-01-010
SignWriting in Unicode (SWU) Characters and the Font Database

```Welcome to the SignWriting Stream```  
```where we show, teach, and demo.```


## Script
https://github.com/Slevinski/SS-01-010

## Documentation
https://sutton-signwriting.github.io/font-db/

In this episode, I use the VS Code editor, the bash command line, and the Node runtime environment on Windows 10 with the Linux subsystem.

To get started, clone the git repository

    > git clone https://github.com/sutton-signwriting/font-db.git 

Next enter the directory and install.  
This will take a while.  Keep reading...

    > cd font-db
    > npm install

We will be using the SignWriting in Unicode (SWU) character set.  I have the SuttonSignWritingOneD font locally installed and I am using the Firefox browser.
𝠀񀀒񀀚񋠥񋡩𝠃𝤝𝤪񋡩𝣷𝤊񀀒𝤈𝣡񋠥𝤍𝤃񀀚𝣯𝣪

To use SWU characters for development, you need to take a few extra steps.

First, install the Sutton SignWriting One-D Font.
* https://slevinski.github.io/SuttonSignWriting/components/fonts.html

Second, configure VS Code to properly display SWU characters in one dimension.  
File >> Preferences >> Settings

Search for "font family".  
Append SuttonSignWritingOneD to the list of fonts.  
Restart VS Code.

Use CSS to force a browser to use the correct font.
<p style="font-family:SuttonSignWritingOneD">𝠀񀀒񀀚񋠥񋡩𝠃𝤝𝤪񋡩𝣷𝤊񀀒𝤈𝣡񋠥𝤍𝤃񀀚𝣯𝣪</p>

If you can see the SWU characters on both sides, we're ready to begin.

## Explore the Database
    > cd db
    > sqlite3 iswa2010.db

    sqlite> .tables
    sqlite> .schema symbol
    sqlite> select symkey,svg from symbol where id=1;
    sqlite> .quit

    > cd ..

## Use the SWU Functions
    > ls swu

### Individual Symbols
    > node swu/swu-symbol-svg.js 񀀚
    > node swu/swu-symbol-svg.js 񀀚 S10000.svg
    > node swu/swu-symbol-png.js 񀀚
    > node swu/swu-symbol-png.js 񀀚 S10000.png
    > node swu/swu-symbol-png.js 񀀚-CP10Z4 S10000.png

### Completed Signs
    > node swu/swu-sign-svg.js 𝠀񀀒񀀚񋠥񋡩𝠃𝤝𝤪񋡩𝣷𝤊񀀒𝤈𝣡񋠥𝤍𝤃񀀚𝣯𝣪
    > node swu/swu-sign-svg.js 𝠀񀀒񀀚񋠥񋡩𝠃𝤝𝤪񋡩𝣷𝤊񀀒𝤈𝣡񋠥𝤍𝤃񀀚𝣯𝣪 sign.svg
    > node swu/swu-sign-png.js 𝠀񀀒񀀚񋠥񋡩𝠃𝤝𝤪񋡩𝣷𝤊񀀒𝤈𝣡񋠥𝤍𝤃񀀚𝣯𝣪
    > node swu/swu-sign-png.js 𝠀񀀒񀀚񋠥񋡩𝠃𝤝𝤪񋡩𝣷𝤊񀀒𝤈𝣡񋠥𝤍𝤃񀀚𝣯𝣪 S10000.png
    > node swu/swu-sign-png.js 𝠀񀀒񀀚񋠥񋡩𝠃𝤝𝤪񋡩𝣷𝤊񀀒𝤈𝣡񋠥𝤍𝤃񀀚𝣯𝣪-CP10Z4 sign.png
    > node swu/swu-sign-png.js 𝠀񀀒񀀚񋠥񋡩𝠃𝤝𝤪񋡩𝣷𝤊񀀒𝤈𝣡񋠥𝤍𝤃񀀚𝣯𝣪-P10G_black_D_yellow,black_Z4 black.png

### Start the Server
This package includes an example server for the font database.  A simple HTTP server that accepts requests for symbols/signs and returns SVG/PNG images and spelling normalizations.

    font-db> ls server
    font-db> node server/server.js

# mangakakalot-downloader
Python script to download manga from mangakakalot

## Install dependencies
Either run `pip install -r requirements.txt` or manually install the dependencies, which are
```
pip install requests
pip install beautifulsoup4
pip install Pillow
```
(Note that Pillow is only needed for the `--make-pdf` option)

Everything has been tested on Windows using Python 3.7.3 and the versions of the
dependencies found in `requirements.txt`.

## Optionally, use the exe
If you are running 64-bit windows and don't care much for python,
you can navigate to the realeses and download a prebuilt executable.

## Example usage

### Download using a text file
Make a textfile called `mangalist.txt` with content similar to
```
fj920366
tifr98811554781969
```
Then run the python script as such:
```
./mangakakalot-dl.py --make-pdf download-list mangalist.txt
```

### Download specific manga
You can also run it so you only download one manga
```
./mangakakalot-dl.py --make-pdf download tifr98811554781969
```

### Resume all mangas in the current directory
The command
```
./mangakakalot-dl.py --make-pdf resume-all
```
will look at the given path and see if the directories contain the readme for that specific manga.
If this file is found, it will use the data from it to check for updates and download those. This
is meant for automation, but in hindsight the `download-list` command above is cleaner, but feel free
to use this method instead.

## Additional info
The script is made so that it does not download files that already are downloaded (unless you specify `--redownload`),
this makes it very useful for automation. Basically, set up your `mangalist.txt` and put the command on a schedule using
crontab or something similar. (Note that currently PDF files will be regenerated even if there are no actual updates)

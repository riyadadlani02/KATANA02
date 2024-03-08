

**On Ubuntu**

```
sudo apt update
sudo apt-get install -y python-tk tk-dev libffi-dev libssl-dev pandoc \
	libgmp3-dev libzbar-dev tesseract-ocr xsel libpoppler-cpp-dev libmpc-dev \
	libdbus-glib-1-dev ruby libenchant-2-dev apktool nodejs groff binwalk \
	foremost tcpflow poppler-utils exiftool steghide stegsnow bison ffmpeg \
	libgd-dev less
```

**Setup**

```
python3.7 -m venv env
source env/bin/activate
python setup.py install
```

If things seemed to go wrong during your installation, and you just want a clean 
slate, you can tear down your virtual environment and start again. Note that 
you will need to run `python setup.py install` one more time.

If you're on a very old Ubuntu distribution and had to install Python 3.7
manually, you may need to install `virtualenv` manually, and use `virtualenv`
vice `python3.7 -m venv` like so:

```
pip3.7 install virtualenv
virtualenv env
source env/bin/activate
```

After installation, Katana will still require multiple external dependencies.
The installation of each of these depends on your distribution and package
manager, so an easier solution is to run Katana through Docker. You can read
more about this in the [`docker/`](docker/) directory.


Usage
----------------

Whenever Katana runs, it creates a `results` directory where it stores its 
findings and **artifacts** (files et. al.) that may be generated from units.

Katana will not run if the `results` directory already exists. You can
have Katana automatically remove the `results` directory before it runs with
the `--force` command-line argument.

```bash
katana --force -f "FLAG{.*?}" "RkxBR3t0aGlzX2lzX2FfYmFzZTY0X2ZsYWd9"
```

Known issues
---------------
ModuleNotFoundError: No module named 'colorama' -- Run `pip install colorama`
TypeError: __init__() got a unexpected keyword argument 'choices_method' -- Run `pip uninstall cmd2 && pip install cmd2=="1.0.1"

Framework Methodology
---------------------

Katana works with a "boss -> worker" topology. One thread (the boss) spins off
other threads (the workers) and returns the results once they have all 
completed. Each worker is called a "unit". The unit is what actually goes 
about and accomplishes the task.

To add functionality to Katana, you simply need to create units. 
The boss will then handle them appropriately.



crypto.t9 - Zwedgy, r4j
esoteric.ook - Liikt
esoteric.cow - Drnkn
stego.audio_spectrogram - Zwedgy
stego.dtmf_decoder - Zwedgy
stego.whitespace - l14ck3r0x01
hash.md5 - John Kazantzis
esoteric.jsfuck - Zwedgy
crypto.playfair - voidUpdate
crypto.nato_phonetic - voidUpdate
```

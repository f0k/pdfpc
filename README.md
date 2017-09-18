pdfpc
=====

This is a fork of https://github.com/pdfpc/pdfpc, a GTK based presentation
viewer application for GNU/Linux which allows to display videos embedded in
slides (see the video example presentation at http://pdfpc.github.io/).

The version 3.1.1 currently available in the Debian and Ubuntu repositories
does not include video support yet, and versions 4.0 and beyond require a lot
of dependencies not easily available on Ubuntu LTS versions. I created this
fork to circumvent this problem.

My fork has an ``oldworking-audio`` branch which pins an old version of the
software that compiles easily on Ubuntu 14.04 LTS (and even 12.04 LTS). In
addition, it includes a small modification such that the software can also
play audio files, not just video files.

To compile, install the following packages:
```bash
sudo apt-get install cmake valac-0.16 libgee-dev librsvg2-dev libpoppler-glib-dev libgstreamer0.10-dev libgstreamer-plugins-base0.10-dev libgtk2.0-dev
```
Then either clone my repository and checkout the ``oldworking-audio`` branch,
or download it from https://github.com/f0k/pdfpc/archive/oldworking-audio.zip
and extract it.
Enter the directory and run:
```bash
git submodule init
git submodule update
mkdir build
cd build
cmake ..
make -j4
sudo make install
```

Embedding audio files works the same way as embedding video files, by adding
a file launch link to the PDF. In LaTeX Beamer, for example, you would do:
```latex
\href{run:somefile.mp3?autostart&loop}{\includegraphics[height=0.7\textheight]{placeholder.jpg}}
```
The ``autostart`` and ``loop`` arguments are optional. In any case, playback
can be stopped and restarted by clicking the placeholder image or text.

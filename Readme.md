======================================================================
8/22/15:
Hacking about with mp3 tagging and web lyrics searches
$ cd ~/dev/mp3hacks
$ git clone https://github.com/ok100/lyvi
$ cd lyvi

So lyvi needs Pillow plyr urwid psutil
And plyr need libglyr python-dbus pygobject
And libglyr needs libintl SQLite glib libcurl cmake

But it looks like the real meat is in glyr so I'm ignoring lyvi...

$ sudo port install cmake py27-Pillow py34-Pillow py27-urwid py34-urwid py27-psutil py34-psutil py27-chardet py34-chardet



sudo port select --set cython cython27
sudo port select --set ipython ipython27


# Getting glyr going...
$ cd ~/dev
$ git clone https://github.com/sahib/glyr
$ cd glyr
$ sudo port install sqlite3 glib2-devel
(actually I had to
   $ sudo port deactivate -f glib2
   $ sudo port install glib2-devel)
$ vi CMakeLists.txt
CMAKE_POLICY( SET CMP0003 OLD )
CMAKE_POLICY( SET CMP0042 NEW )
$ mkdir build; cd build
$ cmake ..
$ make && sudo make install

 --- python binding to libglyr
$ cd ~/dev
$ git clone https://github.com/sahib/python-glyr
$ cd python-glyr
$ sudo port install py27-cython py34-cython
$ python setup.py build
$ sudo python setup.py install


Damn, need to update libcurl to v 9.0.0 or better for plyr to work..

also need mutagen python module

 --- mutagen
$ cd ~/dev/mutagen
$ sudo python setup.py install


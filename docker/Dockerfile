FROM yocto/edison:w05-15
ADD base-feeds.conf /etc/opkg/
RUN opkg update
RUN opkg install python-pip bluez5-obex bluez5-dev bluez5-testtools bluez-hcidump bash bison coreutils diffutils e2fsprogs elfutils findutils git iw less libevent-dev lirc nodejs opkg-utils quilt rsync ruby-staticdev screen syslinux tar tcpdump time util-linux-uuidgen uuid vim

# distcc
COPY bluetooth-main.conf /etc/bluetooth/main.conf
RUN curl https://bootstrap.pypa.io/ez_setup.py | python
RUN pip install ipython
RUN pip install evdev
RUN pip install PyBluez
# RUN pip install dbus-python # IOError: [Errno 2] No such file or directory: '/tmp/pip-build-root/dbus-python/setup.py'

# emacs
RUN cd /tmp && wget -O - http://mirrors.ibiblio.org/gnu/ftp/gnu/emacs/emacs-24.5.tar.gz | tar xfz - && cd /tmp/emacs-24.5 && ./configure --without-x && make -j 11 install && cd /tmp && rm -rf /tmp/emacs-24.5
RUN cd /tmp && wget -O -  wget http://ftp.gnu.org/gnu/cpio/cpio-2.11.tar.gz | tar xfz - && cd /tmp/cpio-2.11 && sed -i -e '/gets is a/d' gnu/stdio.in.h &&  ./configure --enable-mt && make -j 12 install
#COPY .wgetrc /home/root/.wgetrc

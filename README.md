# Hex2Bin-2.5

This is a fork of Jacques Pelletier's Hex2bin <https://sourceforge.net/projects/hex2bin/>, which converts Motorola and Intel hex files to binary.

The changes in this fork are minor:
- Fix bug encountered with nonzero argument to `-s` (e.g. `mot2bin -s E000`).
- Updated Makefile for macOS

*Note: A similar project also does hex <-> binary conversions, supports many formats and other features, see: srecord (http://srecord.sourceforge.net/).*

## Building

Run the following commands to install the software in `/usr/local` (*tested on macOS 15*):
```
make all
sudo make install
```
The results should look like this:
```
% make
gcc -c -std=c99 -O2 -Wall -pedantic hex2bin.c -o hex2bin.o
gcc -c -std=c99 -O2 -Wall -pedantic common.c -o common.o
gcc -c -std=c99 -O2 -Wall -pedantic libcrc.c -o libcrc.o
gcc -c -std=c99 -O2 -Wall -pedantic binary.c -o binary.o
gcc -O2 -Wall -o hex2bin hex2bin.o common.o libcrc.o binary.o
gcc -c -std=c99 -O2 -Wall -pedantic mot2bin.c -o mot2bin.o
gcc -O2 -Wall -o mot2bin mot2bin.o common.o libcrc.o binary.o
% sudo make install
strip hex2bin
strip mot2bin
cp hex2bin mot2bin /usr/local/bin
cp hex2bin.1 /usr/local/share/man/man1
```

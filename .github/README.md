## ASCIIpOrtal for MiyooCFW

ASCIIpOrtal is a text based puzzle game in 2D (SDL).

### Build steps:
#### - initialize submodules  
```
git submodule update --init --recursive
```
#### - build libpdcurses.a
- cross-compile via docker (MiyooCFW)  
```
docker run --volume ./:/src/ -it miyoocfw/toolchain-static-<libc>
cd /src/PDCurses/sdl1
make -j$(nproc) libs
exit
```
- nativly (PC-Linux)

```
cd PDCurses/sdl1
make -j$(nproc) libs
cd -
```
#### - build `asciiportal`
- cross-compile via docker (MiyooCFW) 
```
docker run --volume ./:/src/ -it miyoocfw/toolchain-static-<libc>
cd /src
make -j$(nproc) miyoo
exit
```
you can create ipk pkg by passing `IPK=yes` flag to make
- native build (PC-Linux)  
```
make -j$(nproc) linux
```

cocoa-app
=========

Simple CMake-based cocoa app demo. Illustrates a 64bit build for ARM and Intel
using [mulle-make](/mulle-sde/mulle-make) only (no XCode involved, but headers
and libraries are needed still of course).

Also compiles the XIB to NIB.

Forked from [forexample/cocoa-app](/forexample/cocoa-app)

### Usage

```bash
$ mulle-make
Let cmake do a Release build of cocoa-app for SDK Default in "build" ...
$ file ./build/foo.app/Contents/MacOS/foo
./build/foo.app/Contents/MacOS/foo: Mach-O universal binary with 2 architectures: [x86_64:Mach-O 64-bit executable x86_64] [arm64:Mach-O 64-bit executable arm64]
./build/foo.app/Contents/MacOS/foo (for architecture x86_64):	Mach-O 64-bit executable x86_64
./build/foo.app/Contents/MacOS/foo (for architecture arm64):	Mach-O 64-bit executable arm64
$ ./build/foo.app/Contents/MacOS/foo
```

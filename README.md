# Learning_Modern_3D_Graphics_Programming

- [Learning Modern 3D Graphics Programming](https://paroj.github.io/gltut/index.html)
- [alfonse / gltut / ダウンロード — Bitbucket](https://bitbucket.org/alfonse/gltut/downloads/)

## Run Source Code
- `Tutorial 0.3.8`

```
$ sudo apt install -y premake4
```

```
$ cd "Tutorial 0.3.8/glsdk"
$ premake4 gmake
```


## Error and Solution


```
$ premake4 gmake
$ make
...
...
==== Building Tut 01 Main (debug) ====
Creating obj/Debug
tut1.cpp
Linking Tut 01 Main
/usr/bin/ld: ../glsdk/freeglut/lib/libfreeglutD.a(freeglut_window.o): シンボル 'XGetWindowAttributes' への未定義参照です
//usr/lib/x86_64-linux-gnu/libX11.so.6: error adding symbols: DSO missing from command line
collect2: error: ld returned 1 exit status
Tut 01 Main.make:85: ターゲット 'Tut 01 MainD' のレシピで失敗しました
make[1]: *** [Tut 01 MainD] エラー 1
Makefile:20: ターゲット 'Tut 01 Main' のレシピで失敗しました
make: *** [Tut 01 Main] エラー 2
```

このエラーを解決するには`

`Tutorial 0.3.8/framework/framework.lua`ファイルの中の以下の箇所を変更します。それで解決するはずです。
念の為、編集前に`framework.lua`を`framework.org.lua`に変更しておきましょう。

```
$ cp "Tutorial 0.3.8/framework/framework.lua" "Tutorial 0.3.8/framework/framework.org.lua"
```

```
変更箇所
 79       configuration "linux"
 80           links {"GL", "GLU"}
```

```
$ diff framework.org.lua framework.lua 
80c80
<          links {"GL", "GLU"}
---
>          links {"GL", "GLU", "X11"}
```


## Reference
- https://github.com/xbpeng/DeepTerrainRL/blob/ed82e2ebe5f14fa875cc3d0a2180c64980408e8f/premake4.lua




# how-to-install-mlterm-mac

I'm trying to install mlterm on MacOS with BiDi. BiDi does not actually work right now. So these are just notes until I get get back to this later.


## Links

https://gist.github.com/saitoha/3377f59b0bf87882f319

## Procedure

Assumes Homebrew, and the font [DejaVu Sans Mono](https://github.com/dejavu-fonts/dejavu-fonts) (needed for Arabic) are installed.

Install Fribidi:

```
brew install fribidi
```

Clone mlterm repo:

```
https://github.com/arakiken/mlterm.git
```

## Install

Configure:

```
./configure --prefix=/usr/local --with-gui=quartz
```

It doesn't actually find Fribidi. In the output I see:

```
Mlterm was configured as follows

Installation path prefix          : /usr/local
Build shared libraries            : yes
Build static libraries            : yes
GUI toolkit                       : quartz
BiDi rendering (Fribidi)          : no
```

I also tried `configure` with the options `--enable-fribidi` and `--enable-otl`

Compile:

```
make
```

Install:

```
sudo make install
sudo cp -pvr cocoa/mlterm.app /Applications/
sudo mkdir -p /Applications/mlterm.app/Contents/MacOS
sudo HOME=/Applications cocoa/install.sh /usr/local
```

## Configure apperance

Make `.mlterm` dir:

```
mkdir $HOME/.mlterm
```

Add the following files:

`$HOME/.mlterm/color`:

```
blue=#6699ff
hl_blue=#6699ff
green=#66ff66
hl_green=#66ff66
red=#ff6666
hl_red=#ff6666
yellow=#ffd314
hl_yellow=#ffd314
magenta=#9b4fff
hl_magenta=#9b4fff
```

`$HOME/.mlterm/font`:

```
ISO10646_UCS4_1 = DejaVu Sans Mono;
ISO10646_UCS4_1_BIWIDTH = Hiragino Kaku Gothic ProN;
```

`$HOME/.mlterm/main`:

```
fg_color = white
bg_color = black
alpha = 160
fontsize = 18
scrollbar_mode = right
use_variable_column_width = false
use_combining = true
use_dynamic_comb = true
col_size_of_width_a = 1
logsize = 4096
```

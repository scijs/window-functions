# window-function

[![Build Status](https://travis-ci.org/scijs/window-function.svg?branch=master)](https://travis-ci.org/scijs/window-function) [![npm version](https://badge.fury.io/js/window-function.svg)](http://badge.fury.io/js/window-function)  [![Dependency Status](https://david-dm.org/scijs/window-function.svg)](https://david-dm.org/scijs/window-function)


Window functions for digital signal processing

# Introduction

Among other uses, [window functions](http://en.wikipedia.org/wiki/Window_function) help control [spectral leakage](http://en.wikipedia.org/wiki/Spectral_leakage) when doing Fourier Analysis. This collection of window functions is copied directly from Wikipedia. Caveat emptor.

## Usage

Apply window to a signal:

```javascript
var blackmanHarris = require('window-function/blackman-harris')
var applyWindow = require('window-function/apply')

var signal = [-1, 0, 1, 0, -1, 0]

var windowedSignal = applyWindow(signal, blackmanHarris)
```

Apply the window functions yourself:

```javascript
var wfuncs = require('window-function')

var value = wfuncs.blackmanHarris( 50, 101 )
```

## API

### `require('window-funciton/<type>')(i, total)`

To calculate the value of a window function, pass the sample number `i` and `total` number of samples to one of the window functions listed below, along with any additional parameters it may require. The plots below are calculated from the npm module and plotted with Fourier transform to illustrate the spectral leakage. See [the Wikipedia page on window functions](http://en.wikipedia.org/wiki/Window_function) for more details.

- [Bartlett-Hann](#bartletthann-i-n-)
- [Bartlett](#bartlett-i-n-)
- [Blackman-Harris](#blackmanharris-i-n-)
- [Blackman-Nuttall](#blackmannuttall-i-n-)
- [Cosine](#cosine-i-n-)
- [Exact Blackman](#exactblackman-i-n-)
- [Flat top](#flattop-i-n-)
- [Gaussian](#gaussian-i-n-sigma-)
- [Hamming](#hamming-i-n-)
- [Hann](#hann-i-n-)
- [Lanczos](#lanczos-i-n-)
- [Nuttall](#nuttall-i-n-)
- [Rectangular](#rectangular-i-n-)
- [Triangular](#triangular-i-n-)
- [Tukey](#tukey-i-n-alpha-)
- [Welch](#welch-i-n-)


#### `bartlettHann( i, N )`:

![Bartlett-Hann Window Equation 1](docs/equations/bartlett-hann-1.png)

![Bartlett-Hann Window Equation 2](docs/equations/bartlett-hann-2.png)

![Bartlett-Hann](docs/plots/bartlett-hann.png)

#### `bartlett( i, N )`:

![Bartlett](docs/plots/bartlett.png)

#### `blackman( i, N )`:

![Blackman Window Equation 1](docs/equations/blackman-1.png)

![Blackman Window Equation 2](docs/equations/blackman-2.png)

![Blackman](docs/plots/blackman.png)

#### `blackmanHarris( i, N )`:

![Blackman-Harris Window Equation 1](docs/equations/blackman-harris-1.png)

![Blackman-Harris Window Equation 2](docs/equations/blackman-harris-2.png)

![Blackman-Harris](docs/plots/blackman-harris.png)

#### `blackmanNuttall( i, N )`:

![Blackman-Nuttall Window Equation 1](docs/equations/blackman-nuttall-1.png)

![Blackman-Nuttall Window Equation 2](docs/equations/blackman-nuttall-2.png)

![Blackman-nuttall](docs/plots/blackman-nuttall.png)

#### `cosine( i, N )`:

![Cosine Window Equation 1](docs/equations/cosine.png)

![Cosine](docs/plots/cosine.png)

#### `exactBlackman( i, N )`:

![Exact Blackman](docs/plots/exact-blackman.png)

The same as the Blackman window, except a0 = 0.42659 a1 = 0.49656, and a2 = 0.076849. These place zeros at the third and fourth sidelobes.

#### `flatTop( i, N )`:

![Flat top Window Equation 1](docs/equations/flattop-1.png)

![Flat top Window Equation 2](docs/equations/flattop-2.png)

![Flat Top](docs/plots/flattop.png)

#### `gaussian( i, N, sigma )`:

Sigma controls the width of the window.

![Gaussian Window Equation 1](docs/equations/gaussian-1.png)

![Gaussian Window Equation 2](docs/equations/gaussian-2.png)

![Gaussian](docs/plots/gaussian.png)

#### `hamming( i, N )`:

![Hamming Window Equation 1](docs/equations/hamming-1.png)

![Hamming Window Equation 2](docs/equations/hamming-2.png)

![Hamming](docs/plots/hamming.png)

#### `hann( i, N )`:

![Hann Window Equation](docs/equations/hann.png)

![Hann](docs/plots/hann.png)

#### `lanczos( i, N )`:

![Lanczos Window Equation](docs/equations/lanczos.png)

![Lanczos](docs/plots/lanczos.png)

#### `nuttall( i, N )`:
![Nuttall Window Equation 1](docs/equations/nuttall-1.png)

![Nuttall Window Equation 2](docs/equations/nuttall-2.png)

![Nuttall](docs/plots/nuttall.png)

#### `rectangular( i, N )`:

![Rectangular Window Equation](docs/equations/rectangular.png)

![Rectangular](docs/plots/rectangular.png)

#### `triangular( i, N )`:

![Triangular Window Equation](docs/equations/triangular.png)

![Triangular](docs/plots/triangular.png)

#### `tukey( i, N, alpha )`:

A tapered cosine window. Alpha controls the relative width of the flat section. Alpha=0 is rectangular, alpha=1 is Hann.  ![Tukey Window Equation](docs/equations/tukey.png)

![Tukey](docs/plots/tukey.png)

#### `welch( i, N )`:

![Welch Window Equation](docs/equations/welch.png)

![Welch](docs/plots/welch.png)

### `require('window-function/apply')(array, fn)`

Apply a windowing function to an array, modifies an array in-place.

### `require('window-function/generate')(fn, n)`

Generate an array of `n` samples of the window function `fn`.

## Testing

The tests ensure the window functions aren't returning NaN, but it's hard to have confidence in the accuracy with tests. Instead, I opted to focus on visual testing via plots and Fourier Transforms. To generate the plots, run

```bash
$ npm run generate-plots
```

It pipes them through matplotlib. Don't worry. I realize the irony.



## Credits
Window function definitions and equation images from [Wikipedia: Window Function](http://en.wikipedia.org/wiki/Window_function).

(c) 2015 Ricky Reusser. MIT License

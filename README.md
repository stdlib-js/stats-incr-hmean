<!--

@license Apache-2.0

Copyright (c) 2018 The Stdlib Authors.

Licensed under the Apache License, Version 2.0 (the "License");
you may not use this file except in compliance with the License.
You may obtain a copy of the License at

   http://www.apache.org/licenses/LICENSE-2.0

Unless required by applicable law or agreed to in writing, software
distributed under the License is distributed on an "AS IS" BASIS,
WITHOUT WARRANTIES OR CONDITIONS OF ANY KIND, either express or implied.
See the License for the specific language governing permissions and
limitations under the License.

-->


<details>
  <summary>
    About stdlib...
  </summary>
  <p>We believe in a future in which the web is a preferred environment for numerical computation. To help realize this future, we've built stdlib. stdlib is a standard library, with an emphasis on numerical and scientific computation, written in JavaScript (and C) for execution in browsers and in Node.js.</p>
  <p>The library is fully decomposable, being architected in such a way that you can swap out and mix and match APIs and functionality to cater to your exact preferences and use cases.</p>
  <p>When you use stdlib, you can be absolutely certain that you are using the most thorough, rigorous, well-written, studied, documented, tested, measured, and high-quality code out there.</p>
  <p>To join us in bringing numerical computing to the web, get started by checking us out on <a href="https://github.com/stdlib-js/stdlib">GitHub</a>, and please consider <a href="https://opencollective.com/stdlib">financially supporting stdlib</a>. We greatly appreciate your continued support!</p>
</details>

# incrhmean

[![NPM version][npm-image]][npm-url] [![Build Status][test-image]][test-url] [![Coverage Status][coverage-image]][coverage-url] <!-- [![dependencies][dependencies-image]][dependencies-url] -->

> Compute a [harmonic mean][harmonic-mean] incrementally.

<section class="intro">

The [harmonic mean][harmonic-mean] of positive real numbers `x_0, x_1, ..., x_{n-1}` is defined as

<!-- <equation class="equation" label="eq:harmonic_mean" align="center" raw="\begin{align}H &= \frac{n}{\frac{1}{x_0} + \frac{1}{x_1} + \cdots + \frac{1}{x_{n-1}}} \\ &= \frac{\displaystyle n}{\displaystyle\sum_{i=0}^{n-1} \frac{1}{x_i}} \\ &= \biggl( \frac{\displaystyle\sum_{i=0}^{n-1} \frac{1}{x_i}}{\displaystyle n} \biggr)^{-1}\end{align}" alt="Equation for the harmonic mean."> -->

```math
\begin{align}H &= \frac{n}{\frac{1}{x_0} + \frac{1}{x_1} + \cdots + \frac{1}{x_{n-1}}} \\ &= \frac{\displaystyle n}{\displaystyle\sum_{i=0}^{n-1} \frac{1}{x_i}} \\ &= \biggl( \frac{\displaystyle\sum_{i=0}^{n-1} \frac{1}{x_i}}{\displaystyle n} \biggr)^{-1}\end{align}
```

<!-- <div class="equation" align="center" data-raw-text="\begin{align}H &amp;= \frac{n}{\frac{1}{x_0} + \frac{1}{x_1} + \cdots + \frac{1}{x_{n-1}}} \\ &amp;= \frac{\displaystyle n}{\displaystyle\sum_{i=0}^{n-1} \frac{1}{x_i}} \\ &amp;= \biggl( \frac{\displaystyle\sum_{i=0}^{n-1} \frac{1}{x_i}}{\displaystyle n} \biggr)^{-1}\end{align}" data-equation="eq:harmonic_mean">
    <img src="https://cdn.jsdelivr.net/gh/stdlib-js/stdlib@2b632747053b9e357a4663369528fe62b29a6d55/lib/node_modules/@stdlib/stats/incr/hmean/docs/img/equation_harmonic_mean.svg" alt="Equation for the harmonic mean.">
    <br>
</div> -->

<!-- </equation> -->

</section>

<!-- /.intro -->



<section class="usage">

## Usage

```javascript
import incrhmean from 'https://cdn.jsdelivr.net/gh/stdlib-js/stats-incr-hmean@esm/index.mjs';
```

#### incrhmean()

Returns an accumulator `function` which incrementally computes a [harmonic mean][harmonic-mean].

```javascript
var accumulator = incrhmean();
```

#### accumulator( \[x] )

If provided an input value `x`, the accumulator function returns an updated [harmonic mean][harmonic-mean]. If not provided an input value `x`, the accumulator function returns the current [harmonic mean][harmonic-mean].

```javascript
var accumulator = incrhmean();

var v = accumulator( 2.0 );
// returns 2.0

v = accumulator( 1.0 );
// returns ~1.33

v = accumulator( 3.0 );
// returns ~1.64

v = accumulator();
// returns ~1.64
```

</section>

<!-- /.usage -->

<section class="notes">

## Notes

-   Input values are **not** type checked. If provided `NaN` or a value which, when used in computations, results in `NaN`, the accumulated value is `NaN` for **all** future invocations. If non-numeric inputs are possible, you are advised to type check and handle accordingly **before** passing the value to the accumulator function.

</section>

<!-- /.notes -->

<section class="examples">

## Examples

<!-- eslint no-undef: "error" -->

```html
<!DOCTYPE html>
<html lang="en">
<body>
<script type="module">

import randu from 'https://cdn.jsdelivr.net/gh/stdlib-js/random-base-randu@esm/index.mjs';
import incrhmean from 'https://cdn.jsdelivr.net/gh/stdlib-js/stats-incr-hmean@esm/index.mjs';

var accumulator;
var v;
var i;

// Initialize an accumulator:
accumulator = incrhmean();

// For each simulated datum, update the harmonic mean...
for ( i = 0; i < 100; i++ ) {
    v = randu() * 100.0;
    accumulator( v );
}
console.log( accumulator() );

</script>
</body>
</html>
```

</section>

<!-- /.examples -->

<!-- Section for related `stdlib` packages. Do not manually edit this section, as it is automatically populated. -->

<section class="related">

* * *

## See Also

-   <span class="package-name">[`@stdlib/stats-incr/gmean`][@stdlib/stats/incr/gmean]</span><span class="delimiter">: </span><span class="description">compute a geometric mean incrementally.</span>
-   <span class="package-name">[`@stdlib/stats-incr/mean`][@stdlib/stats/incr/mean]</span><span class="delimiter">: </span><span class="description">compute an arithmetic mean incrementally.</span>
-   <span class="package-name">[`@stdlib/stats-incr/mhmean`][@stdlib/stats/incr/mhmean]</span><span class="delimiter">: </span><span class="description">compute a moving harmonic mean incrementally.</span>
-   <span class="package-name">[`@stdlib/stats-incr/summary`][@stdlib/stats/incr/summary]</span><span class="delimiter">: </span><span class="description">compute a statistical summary incrementally.</span>

</section>

<!-- /.related -->

<!-- Section for all links. Make sure to keep an empty line after the `section` element and another before the `/section` close. -->


<section class="main-repo" >

* * *

## Notice

This package is part of [stdlib][stdlib], a standard library with an emphasis on numerical and scientific computing. The library provides a collection of robust, high performance libraries for mathematics, statistics, streams, utilities, and more.

For more information on the project, filing bug reports and feature requests, and guidance on how to develop [stdlib][stdlib], see the main project [repository][stdlib].

#### Community

[![Chat][chat-image]][chat-url]

---

## License

See [LICENSE][stdlib-license].


## Copyright

Copyright &copy; 2016-2024. The Stdlib [Authors][stdlib-authors].

</section>

<!-- /.stdlib -->

<!-- Section for all links. Make sure to keep an empty line after the `section` element and another before the `/section` close. -->

<section class="links">

[npm-image]: http://img.shields.io/npm/v/@stdlib/stats-incr-hmean.svg
[npm-url]: https://npmjs.org/package/@stdlib/stats-incr-hmean

[test-image]: https://github.com/stdlib-js/stats-incr-hmean/actions/workflows/test.yml/badge.svg?branch=v0.2.0
[test-url]: https://github.com/stdlib-js/stats-incr-hmean/actions/workflows/test.yml?query=branch:v0.2.0

[coverage-image]: https://img.shields.io/codecov/c/github/stdlib-js/stats-incr-hmean/main.svg
[coverage-url]: https://codecov.io/github/stdlib-js/stats-incr-hmean?branch=main

<!--

[dependencies-image]: https://img.shields.io/david/stdlib-js/stats-incr-hmean.svg
[dependencies-url]: https://david-dm.org/stdlib-js/stats-incr-hmean/main

-->

[chat-image]: https://img.shields.io/gitter/room/stdlib-js/stdlib.svg
[chat-url]: https://app.gitter.im/#/room/#stdlib-js_stdlib:gitter.im

[stdlib]: https://github.com/stdlib-js/stdlib

[stdlib-authors]: https://github.com/stdlib-js/stdlib/graphs/contributors

[umd]: https://github.com/umdjs/umd
[es-module]: https://developer.mozilla.org/en-US/docs/Web/JavaScript/Guide/Modules

[deno-url]: https://github.com/stdlib-js/stats-incr-hmean/tree/deno
[deno-readme]: https://github.com/stdlib-js/stats-incr-hmean/blob/deno/README.md
[umd-url]: https://github.com/stdlib-js/stats-incr-hmean/tree/umd
[umd-readme]: https://github.com/stdlib-js/stats-incr-hmean/blob/umd/README.md
[esm-url]: https://github.com/stdlib-js/stats-incr-hmean/tree/esm
[esm-readme]: https://github.com/stdlib-js/stats-incr-hmean/blob/esm/README.md
[branches-url]: https://github.com/stdlib-js/stats-incr-hmean/blob/main/branches.md

[stdlib-license]: https://raw.githubusercontent.com/stdlib-js/stats-incr-hmean/main/LICENSE

[harmonic-mean]: https://en.wikipedia.org/wiki/Harmonic_mean

<!-- <related-links> -->

[@stdlib/stats/incr/gmean]: https://github.com/stdlib-js/stats-incr-gmean/tree/esm

[@stdlib/stats/incr/mean]: https://github.com/stdlib-js/stats-incr-mean/tree/esm

[@stdlib/stats/incr/mhmean]: https://github.com/stdlib-js/stats-incr-mhmean/tree/esm

[@stdlib/stats/incr/summary]: https://github.com/stdlib-js/stats-incr-summary/tree/esm

<!-- </related-links> -->

</section>

<!-- /.links -->

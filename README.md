# Which is the fastest Node.js async pattern?

The asynchronous processing of Node.js becomes more and more convenient, and at the same time faster, as the version is upgraded. However, its convenience and speed have a trade-off. In this repository, to what degree a trade-off occurs in each environment of Node.js is visualized using the [DoxBee benchmark](https://github.com/petkaantonov/bluebird/tree/master/benchmark). This will be a great aid to your development.

## TL;DR

<table>
	<thead>
		<tr>
			<td><strong>Node.JS</strong></td>
			<td><strong>V8</strong></td>
			<td><strong>async type</strong></td>
			<td><strong>time(ms)</strong></td>
			<td><strong>memory(MB)</strong></td>
		</tr>
  </thead>
  <tbody>
		<tr>
			<td rowspan="2">v6.16.0</td>
			<td rowspan="2">5.1.281.111</td>
			<td>callback</td>
			<td align="right">110</td>
			<td align="right">24.49</td>
		</tr>
		<tr>
			<td>async/await</td>
			<td align="right">731</td>
			<td align="right">146.29</td>
		</tr>
		<tr>
			<td rowspan="2">v8.15.0</td>
			<td rowspan="2">6.2.414.75</td>
			<td>callback</td>
			<td align="right">144</td>
			<td align="right">28.30</td>
		</tr>
		<tr>
			<td>async/await</td>
			<td align="right">447</td>
			<td align="right">91.31</td>
		</tr>
		<tr>
			<td rowspan="2">v10.15.0</td>
			<td rowspan="2">6.8.275.32-node.45</td>
			<td>callback</td>
			<td align="right">153</td>
			<td align="right">25.84</td>
		</tr>
		<tr>
			<td>async/await</td>
			<td align="right">333</td>
			<td align="right">66.56</td>
		</tr>
		<tr>
			<td rowspan="2">v11.0.0-pre</td>
			<td rowspan="2">7.3.0-node.5 (candidate)</td>
			<td>callback</td>
			<td align="right">166</td>
			<td align="right">23.62</td>
		</tr>
		<tr>
			<td>async/await</td>
			<td align="right">274</td>
			<td align="right">56.10</td>
		</tr>
	</tbody>
</table>


## Node.JS 11.0.0-pre / V8 7.3.0-node.5 (candidate)

```
file                                       time(ms)  memory(MB)
callbacks-baseline.js                           147       24.85
callbacks-suguru03-neo-async-waterfall.js       195       43.86
callbacks-caolan-async-waterfall.js             209       46.39
promises-bluebird-generator.js                  236       34.35
promises-bluebird.js                            252       49.63
promises-native-async-await.js                  277       55.62
generators-tj-co.js                             295       60.26
promises-ecmascript6-native.js                  307       69.44
promises-lvivski-davy.js                        309       90.01
promises-cujojs-when.js                         365       55.25
promises-then-promise.js                        407       72.75
promises-tildeio-rsvp.js                        444       86.48
promises-dfilatov-vow.js                        588      117.81
promises-calvinmetcalf-lie.js                   589      103.96
streamline-generators.js                        656       80.00
promises-obvious-kew.js                         686       59.55
promises-medikoo-deferred.js                    860      111.28
observables-pozadi-kefir.js                     861      137.10
streamline-callbacks.js                         995       96.79
observables-Reactive-Extensions-RxJS.js        1262      171.39
promises-kriskowal-q.js                        3509      292.23
observables-caolan-highland.js                 3848      473.17
observables-baconjs-bacon.js.js                6555      652.24

Platform info:
Linux 4.4.0-87-generic x64
Node.JS 11.0.0-pre
V8 7.3.0-node.5 (candidate)
Intel(R) Core(TM) i7-8700 CPU @ 3.20GHz × 2
```

## Node.JS 10.15.0 / V8 6.8.275.32-node.45

```
file                                       time(ms)  memory(MB)
callbacks-baseline.js                           153       25.84
promises-bluebird-generator.js                  202       36.63
callbacks-suguru03-neo-async-waterfall.js       207       40.98
callbacks-caolan-async-waterfall.js             224       46.12
promises-bluebird.js                            285       46.12
promises-lvivski-davy.js                        328       87.42
promises-native-async-await.js                  333       66.56
promises-then-promise.js                        334       64.21
promises-cujojs-when.js                         350       63.90
promises-ecmascript6-native.js                  351       80.83
generators-tj-co.js                             366       73.55
promises-tildeio-rsvp.js                        408       81.48
promises-calvinmetcalf-lie.js                   506      128.74
promises-dfilatov-vow.js                        679      111.44
streamline-generators.js                        705       84.40
promises-obvious-kew.js                         715       83.38
promises-medikoo-deferred.js                    810      114.87
observables-pozadi-kefir.js                     858      149.16
streamline-callbacks.js                        1113      113.45
observables-Reactive-Extensions-RxJS.js        1350      177.45
observables-caolan-highland.js                 3752      461.60
promises-kriskowal-q.js                        4123      319.90
observables-baconjs-bacon.js.js                5886      535.86

Platform info:
Linux 4.4.0-87-generic x64
Node.JS 10.15.0
V8 6.8.275.32-node.45
Intel(R) Core(TM) i7-8700 CPU @ 3.20GHz × 2
```

## Node.JS 8.15.0 / V8 6.2.414.75

```
file                                       time(ms)  memory(MB)
callbacks-baseline.js                           144       28.30
callbacks-caolan-async-waterfall.js             231       48.38
promises-bluebird.js                            242       47.80
promises-bluebird-generator.js                  242       40.97
callbacks-suguru03-neo-async-waterfall.js       279       48.63
promises-cujojs-when.js                         359       64.32
promises-lvivski-davy.js                        389       90.06
promises-ecmascript6-native.js                  421       92.20
promises-native-async-await.js                  447       91.31
promises-then-promise.js                        462       72.48
generators-tj-co.js                             490       86.15
promises-tildeio-rsvp.js                        492       84.33
promises-dfilatov-vow.js                        748      135.25
promises-obvious-kew.js                         826      121.65
promises-calvinmetcalf-lie.js                   843      161.94
streamline-generators.js                        870       79.19
promises-medikoo-deferred.js                   1027      108.76
observables-pozadi-kefir.js                    1158      142.53
streamline-callbacks.js                        1416       96.54
observables-Reactive-Extensions-RxJS.js        2190      173.97
promises-kriskowal-q.js                        8172      292.39
observables-caolan-highland.js                10936      516.39
observables-baconjs-bacon.js.js               24106      832.02

Platform info:
Linux 4.4.0-87-generic x64
Node.JS 8.15.0
V8 6.2.414.75
Intel(R) Core(TM) i7-8700 CPU @ 3.20GHz × 2
```

## Node.JS 6.16.0 / V8 5.1.281.111

```
file                                       time(ms)  memory(MB)
callbacks-baseline.js                           110       24.49
callbacks-suguru03-neo-async-waterfall.js       177       40.06
callbacks-caolan-async-waterfall.js             180       45.30
promises-bluebird-generator.js                  191       38.87
promises-bluebird.js                            228       47.09
promises-cujojs-when.js                         262       64.25
promises-then-promise.js                        268       66.41
promises-lvivski-davy.js                        307       85.16
promises-tildeio-rsvp.js                        323       88.00
promises-dfilatov-vow.js                        576      119.18
promises-calvinmetcalf-lie.js                   586      161.76
generators-tj-co.js                             731      146.29
promises-obvious-kew.js                         810      110.66
promises-ecmascript6-native.js                  874      144.22
promises-medikoo-deferred.js                   1264      145.03
observables-Reactive-Extensions-RxJS.js        1434      250.27
streamline-generators.js                       1467      121.52
streamline-callbacks.js                        2322      209.94
promises-kriskowal-q.js                        7943      453.51
observables-baconjs-bacon.js.js               16689      825.02
observables-pozadi-kefir.js                   34186      154.47
observables-caolan-highland.js               109155      493.84
promises-native-async-await.js                  OOM         OOM

Platform info:
Linux 4.4.0-87-generic x64
Node.JS 6.16.0
V8 5.1.281.111
Intel(R) Core(TM) i7-8700 CPU @ 3.20GHz × 2
```


- https://v8.dev/blog/fast-async
- https://github.com/petkaantonov/bluebird/tree/master/benchmark
- https://spion.github.io/posts/analysis-generators-and-other-async-patterns-node.html

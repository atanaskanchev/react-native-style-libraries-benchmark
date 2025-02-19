# React Native Style Libraries Benchmark

Original reproducer was created by @tj-mc: https://github.com/tj-mc/styled-components-native-perf-reproducer

This is an Expo SDK 49 App reproducer to demonstrate the performance difference between popular style libraries and react-native built-in styling.

Tests include React Native `StyleSheet`, `Styled Components`, `Tamagui`, `NativeWind`, `Emotion`, `Zephyr`, `Dripsy`, `Gluestack` and Shopify `restyle`

Feel free to fork or PR this repo with improvements or to include other styling libraries.

### ***Note: Test scores may vary between different machines with different hardware***

### Note: `Tamagui` scores are surprisingly low, I've created a [discussion about it](https://github.com/tamagui/tamagui/discussions/1471)

1000 items are rendered in `Array.map` to simulate the complexity of a real app.

Read this comment on how to test the performance: https://github.com/styled-components/styled-components/issues/3940#issuecomment-1630244738

![demo.png](assets/demo.png)

## Results - Rendering Time for 1000 Empty Views (ms)

Mac Specs: 
Mac Studio M1 Ultra 1TB SSD 64GB RAM\
Simulator: iPhone 13, iOS 16.4

![graph_1.png](assets/graph_1.png)\
![graph_2.png](assets/graph_2.png)

|            | 1     | 2     | 3     | 4     | 5     | 6     | Avg    | % Slowdown |
|------------|-------|-------|-------|-------|-------|-------|--------|------------|
| Native     | 140.1 | 135.6 | 137.5 | 142.1 | 137.2 | 131.3 | 137.6  | 0          |
| Restyle    | 186.8 | 162.3 | 185.2 | 184.4 | 186.6 | 184.2 | 182.5  | 32.63%     |
| Zephyr     | 198.4 | 200.2 | 203.6 | 200.7 | 195.8 | 202.5 | 200.2  | 45.47%     |
| Styled v6  | 227.7 | 226.7 | 229   | 226   | 224   | 225.9 | 226.7  | 64.86%     |
| Emotion    | 280.1 | 281.7 | 277.5 | 282   | 278.2 | 285   | 280.9  | 104.8%     |
| NativeWind | 291.3 | 289   | 295.6 | 293.9 | 292.6 | 294   | 292.9  | 112.3%     |
| Tamagui    | 310   | 318   | 310   | 305   | 324   | 313   | 314.33 | 128.57%    |
| Dripsy     | 661.5 | 651.3 | 665.1 | 661.4 | 653.6 | 673.7 | 661.1  | 380.53%    |
| Gluestack  | 793   | 789   | 815   | 815   | 783   | 779   | 798.83 | 480.24%    |


# Reproduction Steps
1. Start the profiler by pressing Shift + M and open React Dev Tools.
2. Open profiler and hit record
3. Press the toggle button and stop recording
4. Record the time to render App.ts
5. Average the result across at least 3 runs


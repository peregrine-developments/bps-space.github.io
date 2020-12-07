---
title: IMU Selection Guide
parent: Electronics
---

# *How to choose an IMU* 
* Don't consider price as your main deciding factor, the cheapest option might still have the worst price/performance.
* Consider expected G loads, then double or triple for safety margins.
* Lower drift figures are usually better but be wary of incorrectly reported measurements.
* Bosch and ST have FAR better sensing topology than Invensense almost as a rule
* Note that the BNO055 has onboard sensor processing you pay extra for that will NOT work in a rocket context, buy the BMX055. 
* Consider ditching breakout boards, instead design your own integration on board, follow the datasheet recommended schematic and layout.
* Breakouts being attached to your board can lead to sensor decoupling sensed motion from your airframe due to waffling around which is why we don't really recommend using them even though it seems easier. SMD soldering is a useful skill and opens the door to much more accurate sensor implementations.


## **DO NOT USE THE MPU SERIES. Their sensing technology is ancient, drifts more than than Initial D, has incorrect datasheet representation, and useless DMP.** 

## Supply your sensors with a clean, quiet, and correct voltage reference for best results

| IMU Name | Price | DOF | Ranges | Precision | Drift figures | Library? | Recommended |
| ---      | ---   |---  |---      |---        |---            |---       |---|   
| MPU6050 | $2 (EOL) | 6 (Acc/Gy) | ±16g  ±2000°/sec | 16Bit | ±50mg(up to ±80mg) ±20º/s | Many | Bad drift, bad lifetime, do not use | 
| MPU9250 | $3 (EOL) | 9 (Acc/Gy/Mag) | ±16g  ±2000°/sec | 16Bit | ±50mg(up to ±80mg) ±20º/s | Many | Same sensors as 6050, do not use | 
| LSM9DS1 | $6.70 |  9 (Acc/Gy/Mag) | ±16g  ±2000°/sec ±16gauss | 16Bit | ±90mg(stable) ±30º/s ±1 gauss| Many | Yes, good drift figures and proven architecture | 
| LSM6DS0 | $5.25 |  6 (Acc/Gy/) | ±16g  ±2000°/sec  | 16Bit | ±20mg ±1º/s | Few | Maybe, recommend the LSM9DS1 more due to being proven out and better supported |
| LSM6DS032 | $3.79 |  6 (Acc/Gy/) | ±32g  ±2000°/sec  | 16Bit | ±20mg ±0.5º/s | None | Not yet, brand new sensor and is untested with no libraries | 
| BNO055 | $11.16 |  9 (Acc/Gy/Mag) | ±16g  ±2000°/sec ±13gauss | 16Bit(gyro/mag) 14bit(acc) | ±80mg ±2º/s ±.04 gauss| Multiple | No, built-in sensor fusion fails under flight loads|
| BMX055 | $7.27 |  9 (Acc/Gy/Mag) | ±16g  ±2000°/sec ±13gauss | 16Bit(gyro/mag) 14bit(acc) | ±80mg ±2º/s ±.04 gauss| None | Yes, same sensors as BNO but w/o processor |
| BMI055 | $6.00|  6 (Acc/Gy) | ±16g  ±2000°/sec  | 16Bit | ±80mg ±2º/s | None | Yes, same sensors as BNO w/o magnetometer and processor |
| BMI088 | $7.30 |  6 (Acc/Gy) | ±24g  ±2000°/sec | 16Bit | ±20mg ±1º/s | One | Yes, best choice, good newer sensor with lower drift figures than similar |

There is litererally hundreds of IMUs out there to choose from. Make sure you do your research and follow this guide to find the best one for your project. Keep in mind, once you receive your IMU, you have a lot of software to write to pull orientation out of it. There is no simple way to do this, just do your research and work through it bit by bit. 

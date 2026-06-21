---
tags:
  - maths
  - simulation
date: 2026-06-19
difficulty: Medium
platform: leetcode
---

# Code
1. My Version
```CPP
class Solution {
public:
    double angleClock(const int hour, const int minutes) const noexcept {
        const double ans{
            std::abs(static_cast<double>(6 * minutes) -
                     static_cast<double>(30 * (hour % 12) + 0.5 * minutes))};

        return (ans > 180.0) ? 360 - ans : ans;
    }
};
```
2. Trigonometry
```CPP
class Solution {
public:
    double angleClock(int hour, int minutes) {
        double x = hour + minutes / 60.0;
        double diff = fmod(11.0 * x, 12.0);
        return min(diff, 12.0 - diff) * 30.0;
    }
};
```
   
   
## Pattern
- Mathematic
- Simulation

## Key Decision
- calculate the hour angle{30 *(hour%12)+0.5*minutes} //  *originally*  hour*30 
- calculate the minute angle{6*minutes} // originally 30*minutes/5  - (5*(minutes/10));
- find the minAngle by (minuteAngle - hourAngle)
- if(minAngle < 180.0)?minAnlge : 360-minAngle

## Trap
I wasn't able  to calculate the hour and minutes for following condiitions:-
- when the angle is 0
- when the hour is somehow it gave wrong result 

## Complexity
Time: O(1)
Space: O(1)
Why: need to run exactly one two line of code for any size of the the input
	   also need 1 var to store the result and then return the result; 
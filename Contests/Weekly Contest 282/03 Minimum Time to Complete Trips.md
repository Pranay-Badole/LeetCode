# [2187. Minimum Time to Complete Trips](https://leetcode.com/problems/minimum-time-to-complete-trips/)

## Problem Statement:

```
You are given an array time where time[i] denotes the time taken by the ith bus to complete one trip.

Each bus can make multiple trips successively; that is, the next trip can start immediately after completing the current trip.
Also, each bus operates independently; that is, the trips of one bus do not influence the trips of any other bus.

You are also given an integer totalTrips, which denotes the number of trips all buses should make in total.
Return the minimum time required for all buses to complete at least totalTrips trips.
```

## Examples:

```
Example 1:

Input: time = [1,2,3], totalTrips = 5
Output: 3
Explanation:
- At time t = 1, the number of trips completed by each bus are [1,0,0]. 
  The total number of trips completed is 1 + 0 + 0 = 1.
- At time t = 2, the number of trips completed by each bus are [2,1,0]. 
  The total number of trips completed is 2 + 1 + 0 = 3.
- At time t = 3, the number of trips completed by each bus are [3,1,1]. 
  The total number of trips completed is 3 + 1 + 1 = 5.
So the minimum time needed for all buses to complete at least 5 trips is 3.

Example 2:

Input: time = [2], totalTrips = 1
Output: 2
Explanation:
There is only one bus, and it will complete its first trip at t = 2.
So the minimum time needed to complete 1 trip is 2.
```

## Constraints:

```
* 1 <= time.length <= 1e5
* 1 <= time[i], totalTrips <= 1e7
```


<details>
  <summary> CODE </summary>
  
  ```cpp

// BS on answer concept
// here do BS on time and check if that time satisfies 

#define ll long long

class Solution {
public:
    long long minimumTime(vector<int>& v, int t) {
        ll l = 1, r;
        ll ans, mx = 0;
        for(auto &x : v){
            mx = max(mx, (ll)x);
        }
        r = (mx * t) + 100;
        while(l <= r){
            ll mid = l + (r - l)/2;
            ll tot = 0;
            for(int i = 0; i < v.size(); i++) {
                tot += (mid / v[i]);
            }
            if(tot >= (ll)t){
                ans = mid;
                r = mid - 1;
            }
            else{
                l = mid + 1;
            }
        }
        return ans;
    }
};
  
  ```
  
</details>
# Leetcode-134.-Gas-Station
# Description
There are n gas stations along a circular route, where the amount of gas at the ith station is gas[i].

You have a car with an unlimited gas tank and it costs cost[i] of gas to travel from the ith station to its next (i + 1)th station. You begin the journey with an empty tank at one of the gas stations.

Given two integer arrays gas and cost, return the starting gas station's index if you can travel around the circuit once in the clockwise direction, otherwise return -1. If there exists a solution, it is guaranteed to be unique.
# Solution
So in the given problem, we have been given two arrays:

gas → gas[i] represents the amount of gas available at the i-th station.

cost → cost[i] represents the amount of gas needed to travel from station i to station (i+1) in a circular route.

We have to return the starting gas station’s index from which we can travel around the circuit once in a clockwise direction, or -1 if it’s impossible.

Example:

gas  = [1, 2, 3, 4, 5]

cost = [3, 4, 5, 1, 2]

sum(gas) = 15, sum(cost) = 15 → possible.

i=0: total = -2 → reset → res=1

i=1: total = -2 → reset → res=2

i=2: total = -2 → reset → res=3

i=3: total = 3

i=4: total = 6

Output: 3
# Algorithm
1. Firstly check if the sum of gas is less than or greater than the sum of cost . If the total gas available in all stations is less than the total cost, then it’s impossible to travel the full circuit.
2. If total gas is enough, then there is exactly one valid starting index.
3. Set total = 0, res = 0.
4. Use a for loop which checks if the sum of the difference of gas[i] and cost[i] is less than 0.
5. If it is less than 0 then reset total as 0 and increment the res pointer to the next position(i+1).
6. Return res
# Code
class Solution:

    def canCompleteCircuit(self, gas: List[int], cost: List[int]) -> int:
        if sum(gas)<sum(cost):
            return -1
        total=0
        res=0
        for i in range(len(gas)):
            total+=gas[i]-cost[i]
            if total<0:
                total=0
                res=i+1
        return res
# Complexity
Time Complexity:

We traverse the gas and cost arrays once in the loop → O(n).

We also compute sum(gas) and sum(cost), which each take O(n).

Overall complexity = O(n) + O(n) = O(n).

Space Complexity:

We use only a constant number of extra variables (total, res, loop index) → O(1) space.

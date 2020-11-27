# AI-Pacman-Tracking
>1. Exact Inference Observation
- xác định công thức tính toán vị trí khoảng cách (pacman sẽ khoang tròn khoảng cách so với con ma)
```
allPossible[p] = (self.beliefs[p] * emissionModel[trueDistance])
```
>2. Exact Inference with Time Elapse
- lấy tất cả vị trí của ghost trong mê cung:
```
allPossible = util.Counter()
```
- tìm kiếm bị trí mới của Ghost và từ đó tìm ra bị trí cần đi tới tiêp theo:
```
newGhostPosition = self.setGhostPosition(gameState, position)
newDistribution = self.getPositionDistribution(newGhostPosition)
```
- update allPosition:
```
for newPosition, probability in newDistribution.items():
  allPossible[newPosition] += (self.beliefs[position] * probability)
```
>3. Exact Inference Full Test
- giả sử các bóng ma di chuyển độc lập, tìm vị trí con ma gần nhất:
```
distance = 100000000000
        ghost = None
        returnAction = None
        for d in livingGhostPositionDistributions:
            tempGhost = d.argMax()
            tempDist = self.distancer.getDistance(pacmanPosition, tempGhost)
            if tempDist < distance:
                ghost = tempGhost
                distance = tempDist
```
- tìm kiếm các con ma còn lại bằng thuật toán trên:
```
distance = 100000000000
        for act in legal:
            tempDist = self.distancer.getDistance(
                ghost, Actions.getSuccessor(pacmanPosition, act))
            if tempDist < distance:
                distance = tempDist
                returnAction = act
        return returnAction
```
>4. Approximate Inference
- 

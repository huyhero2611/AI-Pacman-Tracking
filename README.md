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

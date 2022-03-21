# A* Algorithm pseudocode

The problem is to solve match a 2d picture with a given input. They must match each other with **Minimal steps**. <br>
I'm going to use 2 functions to detemine the cost:
* `h(n)` is left non-inplace node.
* `g(n)` is depth of current move.

then we can generalize our cost function to be `f(n) = h(n) + g(n)`.

```
    Global picture

    Algorithm MatchPicture(input, coordination, visited, depth, pqueue):
        if countMisPlaced(picture, input) = 0 then:
            return depth + 1
        canMoveNodes <- getCanMove(visited, coordination)
        for nodeToMove In canMoveNodes:
            cost <- getCost(input, coordination, depth, nodeToMove)
            Insert to pqueue object of cost with new input image.
        while pqueue is not empty:
            newInput <- pqueue.pop()
            visited.append(newInput.node)
            newCoordination <- getNewCoordination(newInput.node, input) 
            MatchPicture(newInput.image, newCoordination, visited, depth + 1, pqueue)
        
        return nil
```


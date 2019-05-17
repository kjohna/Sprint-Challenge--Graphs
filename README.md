# Sprint Challenge: Graphs

For this Sprint Challenge, you will be traversing a map based on the adventure engine from Week 1 of `Intro to Python`.

Good luck and have fun! :smile:

Note: The `legacy` directory contains an old exercise for archival purposes. You do not need to work on this and it will not be graded.

# Sprint Challenge: Graphs

This challenge allows you to practice the concepts and techniques learned over the past week and apply them in a concrete project. This Sprint explored Graphs. During this Sprint, you studied breadth and depth first traversals and searches along with random graphs.

You are provided with a pre-generated graph consisting of 500 rooms. You are responsible for filling `traversalPath` with directions that, when walked in order, will visit every room on the map at least once.

## Instructions

**Read these instructions carefully. Understand exactly what is expected _before_ starting this Sprint Challenge.**

This is an individual assessment. All work must be your own. Your challenge score is a measure of your ability to work independently using the material covered through this sprint. You need to demonstrate proficiency in the concepts and objectives introduced and practiced in preceding days.

You are not allowed to collaborate during the Sprint Challenge. However, you are encouraged to follow the twenty-minute rule and seek support from your PM and Instructor in your cohort help channel on Slack. Your work reflects your proficiency graphs and your command of the concepts and techniques from this week's material.

You have three hours to complete this challenge. Plan your time accordingly.

## Commits

Commit your code regularly and meaningfully. This helps both you (in case you ever need to return to old code for any number of reasons and your project manager.

## Description

Open `adv.py`. There are four parts to the provided code:

- World generation code. Do not modify this!
- An incomplete list of directions. Your task is to fill this with valid traversal directions.
- Test code. Run the tests by typing `python3 adv.py` in your terminal.
- REPL code. You can uncomment this and run `python3 adv.py` to walk around the map.

You may find the commands `player.currentRoom.id`, `player.currentRoom.getExits()` and `player.travel(direction)` useful.

To solve this path, you'll want to construct your own traversal graph. You start in room `0`, which contains exits `['n', 's', 'w', 'e']`. Your starting graph should look something like this:

```
{
  0: {'n': '?', 's': '?', 'w': '?', 'e': '?'}
}
```

Try moving south and you will find yourself in room `5` which contains exits `['n', 's', 'e']`. You can now fill in some entries in your graph:

```
{
  0: {'n': '?', 's': 5, 'w': '?', 'e': '?'},
  5: {'n': 0, 's': '?', 'e': '?'}
}
```

You know you are done when you have exactly 500 entries (0-499) in your graph and no `'?'` in the adjacency dictionaries. To do this, you will need to write a traversal algorithm that logs the path into `traversalPath` as it walks.

## Hints

There are a few smaller graphs in the file which you can test your traversal method on before committing to the large graph. You may find these easier to debug.

Start by writing an algorithm that picks a random unexplored direction from the player's current room, travels and logs that direction, then loops. This should cause your player to walk a depth-first traversal. When you reach a dead-end (i.e. a room with no unexplored paths), walk back to the nearest room that does contain an unexplored path.

You can find the path to the shortest unexplored room by using a breadth-first search for a room with a `'?'` for an exit. If you use the `bfs_path` code from the homework, you will need to make a few modifications.

1. Instead of searching for a target vertex, you are searching for an exit with a `'?'` as the value. If an exit has been explored, you can put it in your BFS queue like normal.

2. BFS will return the path as a list of room IDs. You will need to convert this to a list of n/s/e/w directions before you can add it to your traversal path.

If all paths have been explored, you're done!

## Minimum Viable Product

- **1**: Tests do not pass
- **2**: Tests pass with `len(traversalPath) < 2000`
- **3**: Tests pass with `len(traversalPath) < 1000`

## Stretch Problems

It is very difficult to calculate the shortest possible path that traverses the entire graph. Why?
There are as many as 4 possible directions to move at each intersection, changing one choice affects the outcome of the entire puzzle. Exploring all the possible choices is n!, for 500 rooms it would take quite some time to try every possibility.

My best path is 957 moves. Can you find a shorter path?

least moves: 966, shortest path:
['e', 's', 'e', 's', 'n', 'w', 's', 's', 's', 's', 's', 'e', 's', 's', 's', 's', 's', 's', 's', 'n', 'n', 'w', 's', 'n', 'e', 'n', 'n', 'e', 's', 'e', 'e', 's', 's', 'n', 'n', 'w', 's', 's', 'n', 'n', 'w', 's', 's', 'n', 'n', 'n', 'e', 'e', 'n', 'e', 's', 's', 'n', 'n', 'e', 'e', 'w', 's', 's', 's', 's', 'n', 'n', 'e', 'w', 'n', 'n', 'w', 'w', 's', 'w', 'w', 'w', 'n', 'w', 's', 's', 'n', 'n', 'e', 'n', 'n', 'w', 's', 'n', 'n', 'n', 'n', 'e', 's', 's', 'n', 'n', 'e', 's', 'e', 'n', 'e', 's', 's', 'n', 'n', 'w', 's', 'w', 's', 's', 's', 's', 'e', 'w', 'n', 'n', 'n', 'e', 's', 'e', 'w', 's', 'e', 'e', 'e', 'e', 'w', 'w', 'w', 'w', 'n', 'n', 'w', 'n', 'n', 'w', 'w', 'n', 'w', 'w', 's', 'w', 'e', 's', 'w', 'w', 's', 'n', 'e', 'e', 's', 'w', 'e', 's', 'w', 'e', 's', 'w', 's', 's', 'n', 'w', 's', 'n', 'e', 'e', 's', 's', 's', 'n', 'n', 'n', 'w', 'n', 'w', 'n', 's', 'e', 'e', 'e', 's', 's', 's', 's', 's', 'n', 'n', 'n', 'n', 'n', 'n', 'n', 'n', 'n', 'n', 'w', 'w', 'e', 'e', 'e', 'n', 'n', 'e', 'w', 'n', 'n', 'w', 'w', 'w', 'w', 'w', 'w', 's', 'w', 's', 'w', 'w', 'w', 's', 'w', 'w', 'e', 's', 'e', 's', 's', 'w', 'n', 'w', 'e', 's', 'e', 'e', 's', 'w', 'w', 's', 'w', 's', 'n', 'e', 'n', 'e', 'e', 'e', 'e', 'e', 's', 'w', 'w', 'w', 's', 's', 'w', 's', 's', 's', 'w', 'w', 'e', 'e', 's', 'n', 'n', 'w', 'e', 'n', 'w', 'e', 'n', 'w', 'w', 'w', 'e', 'e', 'e', 'e', 's', 's', 's', 's', 'e', 'w', 'n', 'e', 'w', 'n', 'n', 'n', 'n', 'w', 'w', 'e', 'e', 'n', 'w', 'e', 'e', 'e', 's', 'w', 's', 'n', 'e', 'n', 'e', 'n', 'e', 'n', 'n', 'n', 'n', 'n', 'n', 'e', 'e', 'e', 's', 'e', 'n', 's', 's', 'w', 'e', 'n', 'w', 'w', 's', 'w', 's', 's', 'n', 'n', 'e', 'n', 'e', 'n', 'w', 'w', 's', 'n', 'w', 's', 's', 's', 'w', 'w', 'w', 's', 'w', 'n', 's', 'e', 'n', 'e', 'e', 'n', 'w', 'w', 'w', 'e', 'e', 'e', 's', 'e', 's', 'w', 'w', 'e', 's', 'w', 'e', 'n', 'e', 's', 's', 's', 's', 's', 's', 's', 's', 'w', 'e', 'n', 'e', 's', 'n', 'e', 's', 's', 's', 'w', 'e', 'n', 'e', 'w', 'n', 'n', 'w', 'w', 'n', 'n', 'n', 'w', 's', 'w', 's', 'w', 'e', 's', 'w', 'e', 'n', 'n', 'e', 's', 's', 'n', 'n', 'n', 'e', 'n', 'n', 'w', 'w', 'w', 'n', 's', 'w', 'n', 'w', 'n', 'n', 'w', 'n', 'e', 'n', 'w', 'w', 'e', 'n', 's', 'e', 'n', 's', 'e', 'e', 'e', 'n', 'w', 'w', 'e', 'e', 'e', 's', 'n', 'n', 'n', 'w', 'n', 'w', 'e', 's', 'w', 'e', 'e', 's', 'w', 'w', 'w', 'n', 'n', 's', 'w', 'n', 'n', 's', 'w', 'w', 'w', 'e', 'e', 'e', 's', 'w', 's', 'n', 'w', 'e', 'e', 'e', 's', 'w', 'e', 'e', 'e', 'e', 'e', 'n', 's', 'e', 'n', 's', 'e', 'n', 's', 'e', 'e', 'n', 'n', 'w', 'n', 'w', 'n', 's', 'e', 'n', 'n', 'w', 'n', 's', 'w', 'n', 'w', 'e', 's', 'e', 'e', 's', 's', 's', 'w', 'w', 'n', 'n', 'w', 'n', 's', 'e', 's', 's', 'w', 'w', 'n', 'n', 'n', 'n', 'n', 's', 's', 's', 's', 'w', 'n', 'n', 'n', 'n', 'n', 'n', 's', 's', 'w', 'e', 's', 's', 's', 'w', 'w', 'w', 'w', 'w', 'e', 's', 'w', 'e', 'n', 'e', 'e', 'n', 'n', 'n', 's', 's', 'w', 'e', 's', 'e', 'n', 'n', 's', 's', 'e', 's', 'w', 'w', 'e', 'e', 'e', 's', 'e', 'n', 's', 'e', 'e', 'e', 'e', 'e', 's', 'n', 'n', 'n', 'n', 'e', 'e', 'w', 'w', 'n', 'n', 'e', 'w', 'n', 'e', 'n', 'n', 's', 's', 'w', 'w', 'w', 'w', 'n', 'n', 'n', 'n', 's', 's', 's', 'w', 'n', 'n', 'w', 'e', 's', 's', 'e', 's', 'w', 's', 'w', 'e', 'n', 'w', 'n', 's', 'w', 'n', 's', 'e', 'e', 'e', 'e', 'e', 'n', 'n', 's', 'w', 'n', 's', 'e', 's', 'e', 'n', 'n', 'n', 'e', 'n', 'w', 'w', 'e', 'e', 's', 'e', 'n', 'e', 'e', 'w', 'w', 's', 's', 's', 's', 'e', 'n', 'n', 'n', 's', 's', 'e', 'n', 'e', 'n', 'e', 'e', 'w', 's', 'n', 'w', 'n', 's', 's', 'w', 'n', 's', 's', 'w', 's', 's', 'e', 'n', 'e', 'n', 's', 'e', 'n', 's', 'e', 'w', 'w', 'w', 's', 'e', 'w', 'w', 's', 'e', 'w', 'w', 'n', 's', 'w', 'w', 's', 's', 'w', 'n', 'n', 'w', 'n', 'w', 'e', 'e', 'w', 's', 'e', 's', 's', 'e', 's', 's', 'w', 'n', 's', 's', 'w', 'e', 's', 'e', 's', 'e', 'n', 'e', 'n', 'e', 'n', 'e', 'n', 'n', 'n', 's', 'e', 'n', 'n', 'e', 'e', 'e', 'e', 'w', 'n', 's', 'w', 'n', 's', 'w', 'n', 's', 'w', 's', 's', 'w', 's', 's', 'w', 'n', 'n', 'n', 's', 's', 's', 's', 'w', 's', 'w', 'n', 'n', 'e', 'n', 'n', 's', 's', 'w', 'n', 'n', 's', 's', 's', 's', 's', 'e', 'e', 'e', 'e', 's', 'e', 'e', 'e', 'e', 'w', 'n', 's', 'w', 'w', 'w', 'n', 'e', 'e', 'w', 'w', 'w', 's', 'n', 'w', 'n', 'e', 'e', 'e', 'e', 'e', 'e', 's', 'n', 'w', 'w', 'w', 'w', 'w', 'n', 'e', 'n', 'n', 'e', 'e', 'n', 'e', 'w', 's', 'w', 'n', 'n', 'e', 'e', 'e', 's', 'n', 'w', 'w', 'w', 's', 's', 'w', 's', 'e', 'e', 'e', 'e', 'w', 'n', 'e', 'w', 's', 'w', 's', 'e', 'e', 'e', 's', 'n', 'w', 'w', 'w', 'n', 'w', 's', 'n', 'w', 's', 'w', 's', 'w', 's', 'w', 's', 's', 's', 'n', 'n', 'e', 's', 's', 'e', 'w', 'n', 'e', 'e', 's', 's', 's', 'e', 'n', 's', 'e', 'w', 'w', 's', 'e', 'e', 'w', 'w', 's', 'e', 'e', 'w', 'w', 'n', 'n', 'n', 'n', 'e', 'e', 's', 'n', 'e', 'w', 'w', 'w', 'n', 'e', 'e', 'e']

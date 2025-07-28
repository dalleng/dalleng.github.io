+++
date = '2025-07-15T20:14:25-03:00'
title = 'Simple Maze Generation with DFS'
+++

## Intro

I recently came across a simple and clever technique to generate mazes using the [DFS](https://en.wikipedia.org/wiki/Depth-first_search) (Depth-First Search) algorithm.

Traditionally, [DFS](https://en.wikipedia.org/wiki/Depth-first_search) is used to **find a path** through an existing maze—for example, from the entrance to the exit. But I became curious about how DFS could be adapted to *generate* a maze from scratch.

My first instinct was to start with a grid completely filled with walls and then "carve out" a path as we traverse the space. This carving process breaks walls to form valid paths, creating a maze.

Below is an interactive JS project that starts with a fully walled square matrix and runs a basic [DFS](https://en.wikipedia.org/wiki/Depth-first_search) traversal from `(0, 0)` to `(size - 1, size - 1)`. However, this version isn’t quite what we want for maze generation. It tends to go straight toward the goal, producing a single winding path rather than a maze with dead ends and branches.

To generate a more maze-like structure, we need to make a couple of key modifications to the traditional [DFS](https://en.wikipedia.org/wiki/Depth-first_search).

<div id="container" data-height="1000"></div>
<script src="https://cdn.jsdelivr.net/npm/livecodes@0.11.1/livecodes.umd.js"></script>
<script>
  // the UMD version provides the global object `livecodes`
 livecodes.createPlayground('#container', {
    import: 'https://gist.github.com/dalleng/235812f3c59e3e49dd907729f4d69336',
    // other embed options
 });
</script>

## Shuffle the directions

The first tweak that needs to be added is to shuffle the directions in which we move. In order to add randomness to movements, rather than going straight to the exit. Added another interactive JS project with this modification below.
The results look better but not quite right yet.

The first improvement is to shuffle the directions in which [DFS](https://en.wikipedia.org/wiki/Depth-first_search) explores. This adds randomness to the traversal and avoids going straight to the end to make it more maze-like.

Here’s the modified version, shown in the interactive playground below. The results are more interesting, but we’re still not quite there yet.

<div id="container-2" data-height="1000"></div>
<script src="https://cdn.jsdelivr.net/npm/livecodes@0.11.1/livecodes.umd.js"></script>
<script>
  // the UMD version provides the global object `livecodes`
 livecodes.createPlayground('#container-2', {
    import: 'https://gist.github.com/dalleng/5f6af882dee2ad2f161c2f25be93fc5e',
    // other embed options
 });
</script>

## Move 2 steps

The second tweak is to move **two cells at a time** instead of one. We still go up, down, left, or right—but in increments of 2. This lets us leave walls between paths and creates more complex maze structures.

Here’s the final version with both tweaks applied:

<div id="container-3" data-height="1000"></div>
<script src="https://cdn.jsdelivr.net/npm/livecodes@0.11.1/livecodes.umd.js"></script>
<script>
  // the UMD version provides the global object `livecodes`
 livecodes.createPlayground('#container-3', {
    import: 'https://gist.github.com/dalleng/19a69563d587218c85b4846453c6ff19',
    // other embed options
 });
</script>
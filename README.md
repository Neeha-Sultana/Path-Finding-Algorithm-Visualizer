# Path-Finding-Visualizer: - A REACT APPLICATION
 [![NodeJS](https://img.shields.io/badge/node-12.14.1-important)](https://img.shields.io/badge/node-12.14.1-important)
 [![NPM](https://img.shields.io/badge/npm-6.13.7-blueviolet)](https://img.shields.io/badge/npm-6.13.7-blueviolet)
 [![Made With React](https://img.shields.io/badge/made%20with-react-61DAFB)](https://img.shields.io/badge/npm-6.13.7-blueviolet) 
[![Build Status](http://img.shields.io/travis/badges/badgerbadgerbadger.svg?style=flat-square)](https://travis-ci.org/badges/badgerbadgerbadger) 

---------------
### Check out live demo [HERE](https://path-algorithm-visualizer-neeha.netlify.app/)
##### DFS visualization demo:

![dfs](https://github.com/user-attachments/assets/4a9563f2-4c44-4108-a1d0-9aa1bd1c508e)

   


## Overview: 
 This is a fun project on visualizing path finding algorithms i.e BFS, DFS, Dikstra’s , A* algorithm.
This app is entirely built in react and below is the how the interface looks like..
Green box is the starting node and Red box is the end node.
You can see the various algorithms below to visualize.
Here  design of  grid is done using tables and set first node and second node colors using CSS properties.
![full](https://github.com/user-attachments/assets/10f44e5a-bde9-469c-99dd-4b2b521240d1)



## Intro ..

Path finding algorithms plays a vital role in our daily life such as packets in computer networks , google maps uses a path finding algorthm to find the shortest path.
So this project main idea is to visualize this path finding algorthms using react with the help of some css animations.

Let's check out some intuition behind this algorithms for better insights.
### Breadth First Search
* Breadth First Search explores equally in all directions.
* This is an incredibly useful algorithm, not only for regular traversal, but also for procedural map generation, flow field pathfinding, distance maps, and other types of map analysis.
* This may be the algorithm of choice to identify nearby places of interest in GPS.
* BFS guarantees the shortest path.
Below is the result for Breadth first search:
![bfs](https://github.com/user-attachments/assets/abb5ea4f-64ba-4e4c-b112-81e1f268da38)


### Depth First Search
- Traverses by exploring as far as possible down each path before backtracking.
- As useful as the BFS: DFS can be used to generate a topological ordering, to generate mazes, to traverse trees, to build decision trees, to discover a solution path with hierarchical choices…
- DFS does not guarantee the shortest path.
Below is how the DFS works
![dfs](https://github.com/user-attachments/assets/ffe54a13-11a8-4414-887c-ff2d372f93ee)

### Dijkstra
- Dijkstra's Algorithm lets us prioritize which paths to explore. Instead of exploring all possible paths equally, it favors lower cost paths.
- We can assign lower cost to encourage moving on roads while assigning high cost on highway to avoid them.
- It is the algorithm of choice for finding the shortest path paths with multiple destinations.
Below is the demo

![dijkstra](https://github.com/user-attachments/assets/e36c2f5d-56d6-4140-82da-c80c3b7b1e4d)

Now Let's drive into the code ..
------------------
## Getting Started ..
First install node.js which comes with a bundle(npm+npx) to run javascript in local system.
type following commands in the shell to create a react app

```
npx create-react-app my-app
cd my-app
npm start
```

### npm start
Runs the app in the development mode.
Open http://localhost:3000 to view it in the browser.
The page will reload if you make edits.
You will also see any lint errors in the console.
Below is the App.js component which is the root component for the react applications.

```js

import React from 'react';
import './App.css';
import PathfindingVisualizer from './PathfindingVisualizer/PathfindingVisualizer';

function App() {
  return (
    <div className="App">
      <PathfindingVisualizer></PathfindingVisualizer>
    </div>
  );
}

export default App;
```

The PathfindingVisualizer component is imported and rendered in App.js.

I write everything related to the project in the pathfindingVisualizer component.
## pathfindingVisualizer:
Here we jammed everything we need into this component such as GUI logic, animations logic , node objects structure and its properties, Some boolean values (isRunning, isStartNode, isFinishNode, isWallNode ), css properties , walls logic, implementing algorithms, mousehandlers
Then the pathfinding algorithms are written in another folder and is imported into pathfindingVisualizer component.

```js
import React, {Component} from 'react';
import Node from './Node/Node';
import {dijkstra} from '../algorithms/dijkstra';
import {AStar} from '../algorithms/aStar';
import {dfs} from '../algorithms/dfs';
import {bfs} from '../algorithms/bfs';

import './PathfindingVisualizer.css';
```
 Then handle mouse events and some reusable components to make this application more friendly.
 
 There are functionalities in pathfindingVisualizer component for creating initialgrid(), clearwalls(), CreateNode(), isGridClear(), clearGrid() etc ..
 
 ***Below is the driver code to implement algorithms in the component!!***
 
 ```js
 
  visualize(algo) {
    if (!this.state.isRunning) {
      this.clearGrid();
      this.toggleIsRunning();
      const {grid} = this.state;
      const startNode =
        grid[this.state.START_NODE_ROW][this.state.START_NODE_COL];
      const finishNode =
        grid[this.state.FINISH_NODE_ROW][this.state.FINISH_NODE_COL];
      let visitedNodesInOrder;
      switch (algo) {
        case 'Dijkstra':
          visitedNodesInOrder = dijkstra(grid, startNode, finishNode);
          break;
        case 'AStar':
          visitedNodesInOrder = AStar(grid, startNode, finishNode);
          break;
        case 'BFS':
          visitedNodesInOrder = bfs(grid, startNode, finishNode);
          break;
        case 'DFS':
          visitedNodesInOrder = dfs(grid, startNode, finishNode);
          break;
        default:
          // should never get here
          break;
      }
      
 ```


## Deployment

### `npm run build`

Builds the app for production to the `build` folder.<br>
It correctly bundles React in production mode and optimizes the build for the best performance.

The build is minified and the filenames include the hashes.<br>
Your app is ready to be deployed!


I deployed this app in netlify. 
You can check out here : [https://path-algorithm-visualizer-neeha.netlify.app/)





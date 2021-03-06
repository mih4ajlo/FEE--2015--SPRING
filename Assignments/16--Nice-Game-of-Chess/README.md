# 16 -- How About a Nice Game of Chess?

## Description

You're going to implement a chess board that demonstrates the moves from [the Catalan Opening: Closed variation](http://www.chess.com/opening/eco/E06_Catalan_Opening_Closed_Variation), very similar to the interface on Chess.com, maybe most of a game, if you get really far.

## Deliverables

* _WIP Issue:_ `16 -- A Nice Game of Chess` with:
  * checkpoints, features, and estimates!
  * link to the _team_ repo
  * link to the first issue in the team repo
* _WIP Branch:_ `TIY-Chessboard:master`
  * a repository called `TIY-Chessboard`
    * with everyone added as collaborators
  * _multiple commits_ to `TIY-Chessboard:master` made by merging PRs _only_
  * _multiple_ PRs in `TIY-Chessboard`
    * from `feature/` branches to `master`
    * containing multiple commits
    * reviewed by team members
  * Starting with HTML5 Boilerplate, modify:
    * `css/main.css`
    * `index.html`
    * `js/main.js`
* A fully-responsive chessboard with:
  * labels for ranks and files
  * pieces provided via unicode
  * hover states for each piece (not empty squares)
* A responsive interface that provides `<button>`'s for:
  * playing the next move
  * resetting the board
  * playing _all remaining moves_ at once

### BEAST MODE

* Add `<button>`'s for:
  * undoing a move
  * playing through all remaining moves _slowly_
  * pausing playback
* Only use CSS classes for pieces

## Requirements

Work in pairs or trios for this project. One person will create a _new_ repository called `TIY-Chessboard`, then [invite the others as collaborators](https://help.github.com/articles/adding-collaborators-to-a-personal-repository/), Each person must add work to `feature/` branches and open Pull Requests to `master` that are reviewed by peers before being merged. _All commits to `master` **must** be merge commits!_

### Process

There are a _lot_ of moving parts in this assignment, so **spend Thursday planning!**. Plan the work out in "features" -- discrete chunks of functionality -- and estimate them; break down "features" into "tasks" -- bite-size pieces of a "feature". Anything larger than a **Small** should be broken down further. **Write these down** as the first issue in your new repo and _link to it in your WIP Issue_!

Prioritize your feature list according to difficulty and dependency. For example, you can't move pieces on a board until you have pieces. Go figure.

#### Write no code on Thursday!

Draw some diagrams of how the system will work. Collaborate on your old chessboard. Clean up any code you've already written or re-write it together. Build a model of the sytem with strips of paper. Come up with names for things. _Just plan together..._

#### Starting on Friday...

Divvy up the work by tasks and features. Create `feature/` branches for your work. Name them collaboratively. Open PRs early so that others can see what you're working on. When you think you're finished with something, show it to your teammate(s), have them check out your branch (stashing or committing their changes first), and evaluate your progress. If you're working together, ask one of the other teams to take a look. Compare notes frequently with the others. _This is not a competition._

### Implementation

Turn your `print(board)` function into a `toString(board)` function that returns `String` rather than logging it. Replace the `outerHTML` of `#chessboard` with the result of `toString(board)` and ditch all that HTML!

#### Time to wire up the chessboard!

Make buttons across the bottom, side, or top that will increment the board through moves, which are stored as elements in an `Array`.

After each move, update the `#chessboard`. Start by just "refreshing" the `outerHTML` property. Yuck. What about just changing the classes on each cell instead? Maybe you need a `move()` function

#### Add buttons for "rewind" and "fast-forward"...

On "rewind", reset the JavaScript `board` _and_ the `#chessboard` back to the starting position. On "fast-forward", apply all the _remaining_ moves in rapid succession.

#### BEAST MODE

Add a "play" button that will slowly step through each move. **Hint:** Check out the [`WindowTimers` API](https://developer.mozilla.org/en-US/docs/Web/API/WindowTimers) for delaying execution of a function. Add a "pause" button that will stop the automatic playback.

## Notes

How about a nice example:

```html
<html>
  <body>
    <table id="chessboard-kinda">
      <thead>
        <tr>
          <td></td>
          <th> a </td>
          <th> b </td>
          <th> c </td>
          <th> d </td>
          <th> e </td>
          <th> f </td>
          <th> g </td>
          <th> h </td>
        </tr>
      </thead>
      <tbody>
        <tr>
          <th> 1 </th>
          <td class="piece"> R </td>
          <td class="piece"> N </td>
          <td class="piece"> B </td>
          <td class="piece"> Q </td>
          <td class="piece"> K </td>
          <td class="piece"> B </td>
          <td class="piece"> N </td>
          <td class="piece"> R </td>
        </tr>
      </tbody>
    </table>
    <script src="//cdnjs.cloudflare.com/ajax/libs/lodash.js/2.4.1/lodash.min.js"></script>
    <script>

      var table = document.body.children[0],
          thead = document.body.children[0].children[0],
          tbody = document.body.children[0].children[1];

      console.assert(table.tagName == 'TABLE');
      console.assert(thead.tagName == 'THEAD');
      console.assert(tbody.tagName == 'TBODY');

      var chessboard = document.getElementById('chessboard-kinda');

      console.assert(chessboard === table);
      // Shouldn't these be the same?

      // Getting all the rows...
      //
      var rows = document.getElementsByTagName('tr');
      // All the `<tr>` tags...

      console.assert(rows.length === 2);
      // 1 `<tr>` in `<thead>` + 1 `<tr>` in `<tbody>`

      // Getting the row that is a child of `<tbody>`...
      var bodyRow = _.find(rows, { 'parentElement': tbody });

      console.assert(bodyRow === tbody.firstChild);
      // Those should be the same, too, right?

      // Getting some elements via `getElementByClassName`
      var cells = document.getElementsByClassName('piece');

      console.assert(cells.length === 9);
      // 1 `<td>` in `<thead>` + 8 `<tr>` in `<tbody>`

      // Getting the `<td>`'s that are children of `<tbody>`
      var pieces = _.filter(cells, { 'parentElement': bodyRow });

      console.assert(pieces.length === 8);
    </script>
  </body>
</html>
```

## Additional Resources

* [_What is a Leap Year?_ on YouTube](https://www.youtube.com/watch?v=56zlm9qhVGc)
* [Date objects on MDN](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Date)
* [Documentation for Moment.js](http://momentjs.com/docs/)


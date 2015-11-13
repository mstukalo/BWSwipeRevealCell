
# BWSwipeRevealCell

![Example](https://raw.githubusercontent.com/bitwit/BWSwipeRevealCell/master/example.gif)

### Using the library

There are two main classes available - `BWSwipeCell` and `BWSwipeRevealCell`

**BWSwipeCell** - Only contains the pan gesture handling, and is useful mainly for heavy customization through subclassing if all you need is a leg up on swipe interactions

**BWSwipeRevealCell** - Is an out of the box solution that lets you set images and colors for 1 action on the left and right of the table cell. BWSwipeRevealCell is a subclass of BWSwipeCell.


### BWSwipeRevealCell Example
After setting `BWSwipeRevealCell` as your table cell's type in the storyboard and setting a delegate. Use this code in your controller:
```swift
func tableView(tableView: UITableView, cellForRowAtIndexPath indexPath: NSIndexPath) -> UITableViewCell {
    let cell = tableView.dequeueReusableCellWithIdentifier("Cell", forIndexPath: indexPath)
    let swipeCell:BWSwipeRevealCell = cell as! BWSwipeRevealCell
    swipeCell.bgViewLeftImage = UIImage(named:"Done")!.imageWithRenderingMode(.AlwaysTemplate)
    swipeCell.bgViewLeftColor = UIColor.greenColor()
    swipeCell.bgViewRightImage = UIImage(named:"Delete")!.imageWithRenderingMode(.AlwaysTemplate)
    swipeCell.bgViewRightColor = UIColor.redColor()
    swipeCell.type = .SpringRelease
    return cell
}
```

### Customizing through the interface

**var type:BWSwipeCellType**

Can be `.SpringRelease`, `.SwipeThrough` or `.SlidingDoor`. Defaults to `.SpringRelease`

**var revealDirection: BWSwipeCellRevealDirection**

Can be `.Both`, `.Left` or `.Right`. Defaults to `.Both`

**(readonly) var state: BWSwipeCellState**

Can be `.Normal`, `.PastThresholdLeft` or `.PastThresholdRight`

**var threshold: CGFloat**

The point at which pan elasticity starts, and `state` changes. Defaults to the height of the `UITableViewCell` (i.e. when it form a perfect square)

**var progress:CGFloat**

A number between 0 and 1 to indicate progress toward reaching threshold int the current swiping direction

**var shouldExceedThreshold: Bool**

Control whether or not the cell pans past the threshold point

**var panElasticityFactor: CGFloat**

Control how much elasticity there is past threshold, if it can be exceeded. Default is `0.7` and `1.0` would mean no elasticity

**var animationDuration: Double**

Animation duration. Defaults to `0.2`

**weak var delegate: BWSwipeCellDelegate?**

Set the delegate on the cell

### Roadmap
Some brief ideas on ways to improve this library

##### v 0.1.0
- Release as Cocoapod

##### v 0.x.0
- Fix bugs
- More code commentary
- Identify and remove any code redundancy

##### v 1.0.0
- Any breaking changes (protocol, method names etc)

##### v x.0.0
- Customizable interaction per side (i.e. left .SwipeThrough, right .SlidingDoor)
- Possible subclass for allowing .SlidingDoor to convert to .SwipeThrough past a threshold point (see Mail.app)

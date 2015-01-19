# BreakOutToRefresh
Play BreakOut while loading - A playable refresh view using SpriteKit

![](https://raw.githubusercontent.com/dasdom/BreakOutToRefresh/master/PullToRefreshDemo/what.gif)

BreakOutToRefresh uses SpriteKit to add a playable mini game to the pull to refresh view in a table view. In this case the mini game is BreakOut but a lot of other mini games could be presented in this space.

# Installation

Add **BreakOutToRefreshView.swift** to you project.

# Usage

Add this to your table view controller:
```
var refreshView: BreakOutToRefreshView!
  
  override func viewDidLoad() {
    super.viewDidLoad()
    
    let refreshHeight = CGFloat(100)
    refreshView = BreakOutToRefreshView(scrollView: tableView)
    refreshView.delegate = self
    
    tableView.addSubview(refreshView)
    
  }
  
extension DemoTableViewController: UIScrollViewDelegate {
 
  override func scrollViewDidScroll(scrollView: UIScrollView) {
    refreshView.scrollViewDidScroll(scrollView)
  }
  
  override func scrollViewWillEndDragging(scrollView: UIScrollView, withVelocity velocity: CGPoint, targetContentOffset: UnsafeMutablePointer<CGPoint>) {
    refreshView.scrollViewWillEndDragging(scrollView, withVelocity: velocity, targetContentOffset: targetContentOffset)
  }
  
  override func scrollViewWillBeginDragging(scrollView: UIScrollView) {
    refreshView.scrollViewWillBeginDragging(scrollView)
  }
}

extension DemoTableViewController: BreakOutToRefreshDelegate {
  
  func refreshViewDidRefresh(refreshView: BreakOutToRefreshView) {
    // load stuff from the internet
  }

}
```

# Status

This is an alpha version. I hacked it together within a few hours.

# To do

- Add a property to let the developer decide whether the game should end when `endRefreshing()` is called or when the user lifts the finger.
- Add scoring
- Add ending of the game when the ball hits the right wall
- Add different colors
- Add levels

# Author

Dominik Hauser
[App.net: @dasdom](https://alpha.app.net/dasdom)
[Twitter: @dasdom](https://twitter.com/dasdom)
[swiftandpainless.com](http://swiftandpainless.com)

# Licence

MIT

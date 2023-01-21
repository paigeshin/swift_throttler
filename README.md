# swift_throttler

```swift
class Throttler {
    private var searchTask: DispatchWorkItem?
 
    deinit {
        print("Throttler object deiniantialized")
    }
    func throttle(searchText: String, block: @escaping (_ products: [ProductData]) -> Void) {
        searchTask?.cancel()
       let task = DispatchWorkItem { [weak self] in
            guard let obj = self else {
                return
            }
          //  obj.getSearchProducts(searchText: searchText) { (products) in
            //     block(products)
          //  }
          // here you hit the request and get back the data
        }
        self.searchTask = task
        DispatchQueue.main.asyncAfter(deadline: DispatchTime.now() + 0.5, execute: task)
    }
}
```

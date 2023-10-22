# Model 

## Create a `Model` 

> Note: must be a `class`. Marking the class with the `@Model` macro also conforms to the `@ObservableObject` protocol and thus renders UI updates when values change.

```swift
// 1
@Model
final class Counter {
    var currentCount: Int
    
    init(currentCount: Int) {
        self.currentCount = currentCount
    }
}
```

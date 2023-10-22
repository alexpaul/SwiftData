# Model Container 

## Creating a model container instance 

```swift
@MainActor
let sampleContainer: ModelContainer = {
    do {
        let container = try ModelContainer(
            for: Counter.self,
            configurations: ModelConfiguration(
                isStoredInMemoryOnly: false
            )
        )
        if try container.mainContext.fetch(FetchDescriptor<Counter>()).isEmpty {
            let counter = Counter.init(currentCount: 0)
            container.mainContext.insert(counter)
        }
        return container
    } catch {
        fatalError("Could not instantiate model container")
    }
}()
```

# Model Container 

## Creating a model container instance 

```swift
@MainActor
let sampleContainer: ModelContainer = {
    do {
        // 1
        // Create a model container instance
        let container = try ModelContainer(
            for: Counter.self,
            configurations: ModelConfiguration(
                isStoredInMemoryOnly: false
            )
        )
        // 2
        // Check using a `FetchDescriptor` whether the container is empty
        if try container.mainContext.fetch(FetchDescriptor<Counter>()).isEmpty {
            // 3
            // If the container is empty `insert` a new `counter` instance
            let counter = Counter.init(currentCount: 0)
            container.mainContext.insert(counter)
        }
        // 3
        return container
    } catch {
        fatalError("Could not instantiate model container")
    }
}()
```

***

## Inject the `App` with a model container instance via a modifier

```swift
@main
struct SwiftDataPlaygroundApp: App {
    var body: some Scene {
        WindowGroup {
            ContentView()
                // 1
                .modelContainer(sampleContainer)
        }
    }
}
```

***

## Inject a `Preview` with a model container instance 

```swift
#Preview {
    ContentView()
        // 1
        .modelContainer(sampleContainer)
}
```

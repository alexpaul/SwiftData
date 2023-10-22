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

***

## Inject the App with a model container instance via a modifier

```swift
@main
struct SwiftDataPlaygroundApp: App {
    var body: some Scene {
        WindowGroup {
            ContentView()
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
        .modelContainer(sampleContainer)
}
```

# Model Context 

## Create an instance of the model context from the `Environment` 

```swift
struct ContentView: View {
    // 1
    @Environment(\.modelContext) private var modelContext
    
    @Query private var counter: [Counter] = []
    
    var body: some View {
        VStack {
            Button(action: {
                counter[0].currentCount += 1
                modelContext.insert(counter[0])
            }) {
                Text("Count")
            }
            Text("\(counter[0].currentCount)")
        }
        .font(.largeTitle)
    }
}
```

***

## Insert a new object into the model context 

> Note: this operation will autosave to SwiftData

```swift
struct ContentView: View {
    @Environment(\.modelContext) private var modelContext
    
    @Query private var counter: [Counter] = []
    
    var body: some View {
        VStack {
            Button(action: {
                counter[0].currentCount += 1
                // 1
                modelContext.insert(counter[0])
            }) {
                Text("Count")
            }
            Text("\(counter[0].currentCount)")
        }
        .font(.largeTitle)
    }
}
```

# Model Context 

## Using the model context to modify SwiftData objects 

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

## Inserting a new object in the model context 

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

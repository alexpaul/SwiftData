# Query 

## Querying objects from SwiftData 

> Note: Query expects a collection of items

```swift
struct ContentView: View {
    @Environment(\.modelContext) private var modelContext

    // 1 
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

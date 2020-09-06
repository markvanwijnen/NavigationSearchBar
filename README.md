# NavigationSearchBar
An extension to SwiftUI that will add the UISearchController.


## Installation

### Manual:

Update your `Package.swift` file:

```swift
let package = Package(
  ...,

  dependencies: [
    .package(
      url: "https://github.com/markvanwijnen/NavigationSearchBar.git",
      from: "1.0.0"),

    ...
  ],

  ...
)
```

### In Xcode:

1. Go to File > Swift Packages > Add Package Depencency...
2. Enter `https://github.com/markvanwijnen/NavigationSearchBar.git` as the URL
3. Select your desired versioning constraint
4. Click Next
5. Click Finish

## Usage

```swift
import SwiftUI
import NavigationSearchBar

struct ContentView: View {
    @State var text: String = ""
    @State var scopeSelection: Int = 0
    
    var body: some View {
        NavigationView {
            List {
                ForEach(1..<5) { index in
                    Text("Sample Text")
                }
            }
            .navigationTitle("Navigation")
            .navigationSearchBar(text: $text,
                                 scopeSelection: $scopeSelection,
                                 options: [
                                    .automaticallyShowsSearchBar: true,
                                    .obscuresBackgroundDuringPresentation: true,
                                    .hidesNavigationBarDuringPresentation: true,
                                    .hidesSearchBarWhenScrolling: false,
                                    .placeholder: "Search",
                                    .showsBookmarkButton: true,
                                    .scopeButtonTitles: ["All", "Missed", "Other"]
                                 ],
                                 actions: [
                                    .onCancelButtonClicked: {
                                        print("Cancel")
                                    },
                                    .onSearchButtonClicked: {
                                        print("Search")
                                    },
                                    .onBookmarkButtonClicked: {
                                        print("Present Bookmarks")
                                    }
                                 ], searchResultsContent: {
                                    Text("Search Results for \(text) in \(String(scopeSelection))")
                                 })
        }
    }
}

struct ContentView_Previews: PreviewProvider {
    static var previews: some View {
        ContentView()
    }
}

```

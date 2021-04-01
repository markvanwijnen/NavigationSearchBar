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
      from: "1.2.0"),

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
                                     NavigationLink(destination: Text("Destination")) {
                                         Text("Search Results for \(text) in \(String(scopeSelection))")
                                     }
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

## Donate

If you have been enjoying my free Swift package, please consider showing your support by buying me a coffee through the link below. Thanks in advance!

<a href="https://www.buymeacoffee.com/markvanwijnen" target="_blank"><img src="https://cdn.buymeacoffee.com/buttons/v2/arial-yellow.png" height="60px" alt="Buy Me A Coffee"></a>

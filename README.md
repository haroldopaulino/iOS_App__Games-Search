# Games Search iOS App

**Native iOS game-search application built with SwiftUI, async/await networking, MVVM-style state management, JSON decoding, remote image loading, and paginated REST API search against the Giant Bomb games database.**

Games Search is a SwiftUI iOS application that lets users search a large public games database, view matching game titles, and load additional pages of results through pull-to-refresh pagination.

The project demonstrates practical iOS development skills around modern SwiftUI UI composition, asynchronous API calls, REST query construction, typed response models, image loading, and user-driven search behavior.

https://user-images.githubusercontent.com/28379115/184469138-850029e6-e26d-4c72-8e81-07e0fad47cf8.mp4

---

## Why This Project Matters

This repository is a strong iOS portfolio project because it shows a focused, real-world mobile workflow: search, fetch, decode, display, and paginate remote API data.

The project highlights:

- Native iOS development with Swift
- SwiftUI interface implementation
- Searchable navigation UI
- Async/await networking
- URLSession-based REST API calls
- URLComponents query construction
- JSON decoding with `Decodable`
- MVVM-style view model separation
- Observable UI state with `@StateObject` and `@Published`
- Remote image loading with `AsyncImage`
- Pull-to-refresh pagination
- Public API integration
- Xcode project structure with test targets

This is useful for employers because it shows the ability to build an app that consumes real backend data, handles search input, manages asynchronous state, and presents results in a clean native iOS interface.

---

## Project Overview

The app searches the Giant Bomb games API and displays matching games in a SwiftUI list.

The main flow is:

1. The user enters a game name in the search field.
2. The app builds a REST API request with the search term.
3. The app fetches JSON results asynchronously.
4. The response is decoded into typed Swift models.
5. The UI displays game names and images.
6. Pull-to-refresh increments the page number and loads more results.

The original README describes this as a personal exercise to consume a sizeable public API and implement pagination, where each swipe-down action queries more results.

---

## Main Features

### Game Search

The app uses SwiftUI's searchable navigation UI to let users search for games. Search begins after the input reaches a minimum useful length, reducing unnecessary API calls for very short text.

### REST API Integration

The app builds a request to the Giant Bomb games API using `URLComponents` and query parameters for:

- Response format
- Requested fields
- Result limit
- Offset / page behavior
- Name-based filtering

### Async/Await Networking

The `Webservice` class uses Swift concurrency with `async throws` and `URLSession.shared.data(from:)` to fetch search results without blocking the UI.

### JSON Decoding

The app defines typed `Decodable` models for the games response, game records, and image records. This creates a structured mapping between the API response and Swift objects.

### SwiftUI List UI

Search results are displayed in a native SwiftUI `List`. Each row shows the game image and game name.

### Remote Image Loading

The app uses `AsyncImage` to load game artwork from the image URL returned by the API. A progress indicator is displayed while images load.

### Pull-to-Refresh Pagination

The app uses SwiftUI's `.refreshable` modifier to increment the page number and request the next set of results.

### MVVM-Style State Management

The project separates UI and data-fetching state through a `GamesListViewModel`, which owns the published games array and calls the web service.

---

## Technical Stack

| Layer | Technology |
|---|---|
| Platform | iOS |
| Language | Swift |
| UI framework | SwiftUI |
| Networking | URLSession |
| Concurrency | async/await |
| State management | ObservableObject, @StateObject, @Published |
| Data models | Decodable |
| Remote images | AsyncImage |
| API | Giant Bomb games API |
| Project type | Xcode iOS app |
| Tests | XCTest / UI test targets |
| License | GPL-3.0 |

---

## Repository Structure

```text
iOS_App__Games-Search/
├── ApiCall.xcodeproj/
├── ApiCall/
│   ├── Assets.xcassets/
│   ├── Preview Content/
│   ├── ApiCall_SampleApp.swift
│   ├── ContentView.swift
│   ├── Games.swift
│   ├── GamesListViewModel.swift
│   ├── String+Extensions.swift
│   └── Webservice.swift
├── ApiCall SampleTests/
├── ApiCall SampleUITests/
├── iOS_Games_Search.mp4
├── README.md
└── LICENSE
```

---

## Important Source Files

### `ContentView.swift`

Defines the primary SwiftUI interface:

- Navigation view
- Search field
- Game results list
- Remote image display
- Search input handling
- Pull-to-refresh pagination
- Dynamic title updates

### `Games.swift`

Defines the API response models:

- `Games`
- `Game`
- `ImageRecord`

These models decode the game response, result metadata, image URLs, IDs, GUIDs, and game names.

### `GamesListViewModel.swift`

Provides the observable state layer for the UI:

- Owns the published games array
- Performs game searches asynchronously
- Converts decoded `Game` records into view models

### `Webservice.swift`

Handles REST API communication:

- Builds the API URL with `URLComponents`
- Adds query parameters
- Executes the network request with `URLSession`
- Checks HTTP response status
- Decodes JSON into Swift models
- Returns game results to the view model

### `String+Extensions.swift`

Provides helper behavior for string cleanup before using search input in the API query.

---

## Skills Demonstrated

This repository demonstrates several iOS and mobile engineering skills:

- Swift programming
- SwiftUI app development
- Searchable UI design
- REST API consumption
- URLSession networking
- Swift concurrency with async/await
- JSON decoding with Codable/Decodable
- MVVM-style state separation
- ObservableObject-based state updates
- Remote image loading
- Pagination behavior
- Pull-to-refresh interactions
- API query parameter construction
- Xcode project organization
- Test target structure

---

## Product Design Notes

### Search-First User Experience

The app is designed around a direct search workflow. Users can type a game name, immediately see matching results, and load more results with a familiar pull-to-refresh gesture.

### Lightweight Architecture

The code is organized into clear responsibilities:

- `ContentView` handles presentation.
- `GamesListViewModel` manages UI state.
- `Webservice` handles networking.
- `Games` models handle response decoding.

This makes the project easy to understand and extend.

### Real API Usage

The app integrates with a public game database instead of mock data. This makes the project more valuable as a portfolio example because it exercises real network behavior, response decoding, image loading, and pagination.

[https://www.giantbomb.com/api/documentation/#toc-0-17](https://www.giantbomb.com/api/documentation/#toc-0-17)

---

## How to Run

1. Clone the repository.
2. Open `ApiCall.xcodeproj` in Xcode.
3. Select an iOS simulator or connected device.
4. Build and run the app.
5. Search for a game title.
6. Pull down on the results list to load another page of results.

For a production-ready version, move API credentials out of source control and into a secure configuration mechanism.

---

## License

This project is licensed under the GPL-3.0 license.

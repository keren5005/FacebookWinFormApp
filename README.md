# Desktop Facebook Application

## Project Overview

This application provides a Facebook-integrated desktop experience, allowing users to interact with their Facebook profiles to view and post content, manage friends and pages, and utilize additional features like engagement scoring and birthday statistics.

---

## Features

### Basic Functionality
- **User Posts**: View and create posts.
- **User Photos**: Display all photos associated with the user’s profile.
- **Friends List**: View the user's friends.
- **Facebook Groups**: Display all groups to which the user belongs.

### Additional Features
1. **Engagement Metric**: Calculates and displays a score based on the user’s activity, factoring in post count, likes, and comments.
2. **Favorite Pages**: Users can mark favorite pages from their liked pages list, which is saved across sessions.
3. **Birthday Statistics**: Provides statistics about the user’s birthday, including days until the next birthday, days since birth, and age comparisons with five celebrities from different age groups.

---

## Design Patterns

### 1. Decorator Pattern

#### Purpose
The Decorator pattern was chosen to manage a flexible UI for buttons, allowing for multiple button styles and behaviors.

#### Implementation
- **Interface `IDecoratedButton`**: Contains methods `ApplyDecoration()` and `GetControl()` for button styling and control access.
- **Class `BasicButton`**: Implements `IDecoratedButton`, inheriting properties from `System.Windows.Forms.Button`.
- **Decorator Class `ButtonDecorator`**: Contains a `IDecoratedButton` instance, allowing flexible extension.
- **Additional Decorators**:
  - `RoundButton`: Creates buttons with rounded corners.
  - `ColoredFrameButton`: Adds a colored frame to buttons.
  - `ColoredTextButton`: Changes button text color.

*Diagrams: Class Diagram, Sequence Diagram*

### 2. Composite Pattern

#### Purpose
This pattern enables mixed media (photos and videos) to display seamlessly, imitating Facebook’s photo and video albums.

#### Implementation
- **Interface `IMediaItem`**: Defines the `Display()` method for displaying media in a `PictureBox`.
- **Class `UserPhoto`**: Stores photo URL and post date, implementing `IMediaItem`.
- **Class `UserVideo`**: Stores video URL, post date, and includes a `UserPhoto` instance for the video’s thumbnail. Uses `Display()` to show the thumbnail and open the video in a browser.

*Diagrams: Class Diagram, Sequence Diagram*

### 3. Singleton Pattern

#### Purpose
The Singleton pattern ensures a single instance of each manager for data consistency and to avoid data conflicts.

#### Implementation
- **Static Instance and Locking**: A private static variable and a lock ensure only one instance per manager, even in multi-threaded environments.
- **Singleton Classes**:
  - `FacebookFeaturesManager`: Manages Facebook features (posts, photos, friends).
  - `BirthdayStatsManager`: Manages birthday-related statistics.
  - `FavoritePagesManager`: Manages and saves favorite pages.
  - `EngagementScoreManager`: Manages the user’s engagement score.

*Diagrams: Class Diagram, Sequence Diagram*

### 4. Factory Pattern

#### Purpose
The Factory pattern simplifies manager creation by centralizing instance creation, offering flexibility for future additions.

#### Implementation
- **Class `ManagerFactory`**: Creates manager instances based on the requested type (e.g., `BirthdayStatsManager`, `EngagementScoreManager`).
- **Advantages**:
  - Centralized creation logic
  - Flexibility to add new manager types without modifying existing code
  - Handles dependencies for each manager, promoting modularity.

*Diagrams: Class Diagram, Sequence Diagram*

---

## Asynchronous Programming

To improve user experience and performance, asynchronous programming is used in:
- **Loading Posts, Photos, Videos, and Friends**: Fetches data from Facebook servers asynchronously to prevent the UI from freezing.
- **Engagement Score Calculation**: Asynchronous calculation and display to handle large data requests without slowing down the application.

### Implementation
Each asynchronous function uses `await` and a `CallbackHandler`. `CallbackHandler` checks if `Invoke` is needed (i.e., whether the current thread has UI editing permissions). If the current thread is not the UI thread, `Invoke` is called to ensure UI operations are performed on the main thread.

---

## Data Binding

Data Binding was implemented to dynamically link data (like the friend list) to UI elements (e.g., `ListBox`). This approach:
- Automatically updates the UI when data changes, eliminating manual updates.
- Separates data logic from display, improving performance and maintenance.

### Implementation
- **Class `FacebookFeaturesManager`**: Uses `DisplayFriends` to bind the friends list to a `ListBox` via `BindingSource`. The data is fetched asynchronously, and the `ListBox` updates automatically.

---

## Project Structure and Code Examples

- **Main Classes**:
  - `FacebookFeaturesManager`: Central manager for Facebook features.
  - `FavoritePagesManager`: Manages favorite pages with persistence across sessions.
  - `BirthdayStatsManager`: Calculates and displays birthday-related statistics.
  - `EngagementScoreManager`: Computes and displays the user’s engagement score.

- **Button Decorators**:
  ```csharp
  public interface IDecoratedButton { /* ... */ }
  public class BasicButton : Button, IDecoratedButton { /* ... */ }
  public class RoundButton : ButtonDecorator { /* ... */ }
  ```

- **Media Items**:
  ```csharp
  public interface IMediaItem { void Display(PictureBox pictureBox); }
  public class UserPhoto : IMediaItem { /* ... */ }
  public class UserVideo : IMediaItem { /* ... */ }
  ```

- **Asynchronous Example**:
  ```csharp
  public async Task LoadUserPostsAsync()
  {
      await FetchPosts();
      CallbackHandler();
  }
  ```

---

## Getting Started

1. **Clone the Repository**:
   ```bash
   git clone <repository-url>
   ```

2. **Open the Solution in Visual Studio** and set the main project to run.

3. **Build and Run**:
   - Ensure you have Facebook API access credentials.
   - Run the application to interact with your Facebook profile.

---

## Contributing

If you wish to contribute, please submit a pull request or open an issue for discussion. All contributions are welcome, from feature requests to bug fixes.

---

## License

This project is licensed under the MIT License.

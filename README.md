# Facebook Desktop App

A C# .NET WinForms desktop application that utilizes the Facebook API to provide a streamlined interface for viewing friends lists, posts, photos, and more directly from a desktop environment.

## Features

- **Secure Login:** User authentication with Facebook.
- **User Posts & Photos:** View posts and browse photos with navigation buttons.
- **Friends List:** See a list of friends who have logged into the app.
- **Engagement Score:** Displays the user’s Facebook engagement.
- **Favorite Pages Management:** Manage a list of favorite Facebook pages.
- **Birthday Insights:** Fun insights about the user’s birthday and age.

## Screenshots

### App Screenshots

Below are some key screens showcasing the app’s main features:

| Feature               | Screenshot                                                                                         | Description                            |
|-----------------------|----------------------------------------------------------------------------------------------------|----------------------------------------|
| **Login Screen**      | <img src="./pictures/loginScreen.png" width="250">                                                 | Secure Facebook login with profile info |
| **Inside Screen**     | <img src="./pictures/insideScreen.png" width="250">                                                | Main app interface post-login           |
| **Friends List**      | <img src="./pictures/FavoritePages.png" width="250">                                               | Display of user’s friends              |
| **Birthday Insights** | <img src="./pictures/birthdayStats.png" width="250">                                               | Fun birthday insights                  |

## Project Architecture

### Class Diagram

Illustrates the primary classes and their relationships within the app.

<img src="./pictures/classDiagram.png" alt="Class Diagram" width="500">

### Sequence Diagram

Shows the interaction flow for major app features (e.g., login, fetching friends list).

<img src="./pictures/sequenceDiagram.png" alt="Sequence Diagram" width="500">

## Getting Started

### Prerequisites

- .NET Framework (e.g., version 4.8)
- Facebook Developer App ID

### Installation

1. Clone the repository:
   ```bash
   git clone https://github.com/your-username/facebook-desktop-app.git
   cd facebook-desktop-app
   ```

2. Open the project in Visual Studio and add your **Facebook App ID** in the configuration.

3. Build and run the project.

## License

This project is licensed under the MIT License. See the [LICENSE](LICENSE) file for details.


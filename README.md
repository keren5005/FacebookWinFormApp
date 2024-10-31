# Facebook Desktop App

A C# .NET WinForms desktop application that interacts with the Facebook API, providing an easy-to-use interface for viewing friends lists and engaging with Facebook data directly on your Windows desktop.

## Features

- **Secure Login:** Easily log into Facebook within the app using Facebook's authentication.
- **Friends List Display:** View and interact with your Facebook friends in an organized ListBox.
- **Data Binding and Fetching:** Integrated data binding for smooth interaction with Facebook data.
- **Responsive UI:** Designed for an intuitive and seamless desktop experience.

## Getting Started

### Prerequisites

- [.NET Framework](https://dotnet.microsoft.com/download) (version required for your project, e.g., 4.8)
- Facebook Developer Account and App ID (see [Facebook Developer Documentation](https://developers.facebook.com/docs/))

### Installation

1. Clone the repository:
   ```bash
   git clone https://github.com/your-username/facebook-desktop-app.git
   cd facebook-desktop-app
   ```

2. Open the project in Visual Studio.

3. In `App.config`, set your **Facebook App ID**:
   ```xml
   <appSettings>
       <add key="FacebookAppId" value="your_app_id_here"/>
   </appSettings>
   ```

4. Build and run the project in Visual Studio.

### Usage

1. Launch the app and log into Facebook via the secure login screen.
2. Access your friends list and interact with Facebook data.

## Contributing

Contributions are welcome! Please fork the repository, create a new branch, and submit a pull request.

## License

This project is licensed under the MIT License. See the [LICENSE](LICENSE) file for details.


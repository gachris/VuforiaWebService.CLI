# VuforiaWebService.CLI

## Overview

The VuforiaWebService.CLI is a command-line interface tool for interacting with the Vuforia platform. It allows users to manage targets, retrieve data, and perform various operations on the Vuforia database using their access and secret keys.

## Features

- List all targets in the database
- Retrieve details for a specific target
- Insert new targets
- Update existing targets
- Delete targets
- Check for similar targets
- Generate summary reports
- Get a summary of the database

## Prerequisites

- .NET SDK (version 6.0 or higher)
- Vuforia Access Key and Secret Key

## Installation

You have three options for installing the VuforiaWebService.CLI:

### Option 1: Publish the Application

1. Clone the repository:

   ```bash
   git clone https://github.com/gachris/VuforiaWebService.CLI.git
   cd VuforiaWebService.CLI
   ```

2. Restore dependencies:

   ```bash
   dotnet restore
   ```

3. Publish the application:

   ```bash
   dotnet publish --configuration Release --output ./publish --self-contained true --runtime win-x64 -p:PublishSingleFile=true -p:PublishTrimmed=true -p:DebugType=None
   ```

4. After publishing, navigate to the `./publish` directory to find the executable.

### Option 2: Package the Application as a .NET Tool

1. Clone the repository:

   ```bash
   git clone https://github.com/gachris/VuforiaWebService.CLI.git
   cd VuforiaWebService.CLI
   ```

2. Restore dependencies:

   ```bash
   dotnet restore
   ```

3. Package the application as a tool:

   ```bash
   dotnet pack --configuration Release -p:PackAsTool=true -p:ToolCommandName=Vuforia
   ```

4. Install the tool globally from the local source:

   ```bash
   dotnet tool install --global --add-source "C:\Users\chris\source\repos\VuforiaWebService.CLI\nupkgs" VuforiaWebService.CLI
   ```

### Option 3: Install from NuGet.org

You can also install the tool directly from NuGet.org:

1. Open your command line or terminal.

2. Run the following command:

   ```bash
   dotnet tool install --global VuforiaWebService.CLI
   ```

Alternatively, you can find the package on [NuGet.org](https://www.nuget.org/packages/VuforiaWebService.CLI) for more details.


## Usage

To use the Vuforia CLI app, you must provide your access key and secret key as command-line arguments. Below are some examples of how to use the app:

### List All Targets
```bash
vuforia --access-key <your_access_key> --secret-key <your_secret_key> list
```

### Get Target Details
```bash
vuforia --access-key <your_access_key> --secret-key <your_secret_key> get --target-id <target_id>
```

### Insert a New Target
```bash
vuforia --access-key <your_access_key> --secret-key <your_secret_key> insert --target-name "SampleTarget" --target-width 1 --target-image "<path_to_your_image>" --target-active-flag true --target-metadata "<your_target_metadata>"
```

### Update an Existing Target
```bash
vuforia --access-key <your_access_key> --secret-key <your_secret_key> update --target-id <target_id> --target-name "UpdatedTarget" --target-width 1 --target-image "C:\Users\YourUsername\Pictures\sample_image.jpg" --target-active-flag true --target-metadata "This is a sample target for demonstration."
```

### Delete a Target
```bash
vuforia --access-key <your_access_key> --secret-key <your_secret_key> delete --target-id <target_id>
```

### Check for Similar Targets
```bash
vuforia --access-key <your_access_key> --secret-key <your_secret_key> check-similar --target-id <target_id>
```

### Generate a Summary Report
```bash
vuforia --access-key <your_access_key> --secret-key <your_secret_key> summary-report --target-id <target_id>
```

### Get Database Summary
```bash
vuforia --access-key <your_access_key> --secret-key <your_secret_key> database-summary
```

## Parameters Notes

### General Parameters

- **`--access-key <your_access_key>`**: Your Vuforia server access key for authentication.
- **`--secret-key <your_secret_key>`**: Your Vuforia server secret key for authentication.

### Command-Specific Parameters

#### List All Targets
- **No additional parameters needed**.

#### Get Target Details
- **`--target-id <target_id>`**: Unique identifier of the target.

#### Insert a New Target
- **`--target-name "SampleTarget"`**: Name for the new target.
- **`--target-width 1`**: Width of the target in units.
- **`--target-image "<path_to_your_image>"`**: File path to the target image.
- **`--target-active-flag true`**: Activation status of the target.
- **`--target-metadata "<your_target_metadata>"`**: Metadata associated with the target.

#### Update an Existing Target
- **`--target-id <target_id>`**: Unique identifier of the target to update.
- **Other parameters**: Same as for inserting a new target.

#### Delete a Target
- **`--target-id <target_id>`**: Unique identifier of the target to delete.

#### Check for Similar Targets
- **`--target-id <target_id>`**: Unique identifier of the target for similarity checks.

#### Generate a Summary Report
- **`--target-id <target_id>`**: Unique identifier of the target for which to generate a report.

#### Get Database Summary
- **No additional parameters needed**.

### Additional Usage Note
- You can also run the CLI application using the `dotnet` command:
  ```bash
  dotnet run --access-key <your_access_key> --secret-key <your_secret_key> list
  ```

## Important Reminders
- Replace all placeholder values (`<...>`) with your actual Vuforia credentials and target information.
- Handle your access and secret keys securely to prevent unauthorized access to your Vuforia account.

## License

This project is licensed under the MIT License. See the LICENSE file for details.

## Contributing

If you would like to contribute to this project, please fork the repository and submit a pull request.

## Acknowledgements

- [Vuforia](https://developer.vuforia.com/) for providing the AR platform.

### Additional Commands

To uninstall the tool globally:

```bash
dotnet tool uninstall --global VuforiaWebService.CLI
```

To update the tool globally:

```bash
dotnet tool update --global VuforiaWebService.CLI
```
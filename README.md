# CineMemo Lite Launcher

A Bash script for launching the local CineMemo Lite application on Ubuntu and other Linux distributions.

The script opens CineMemo Lite in the default web browser and starts the local Python HTTP server on port `8888`.

## Features

- Checks whether the CineMemo Lite project directory exists.
- Starts the local server using `server.py`.
- Automatically opens the application in the default web browser.
- Displays the local application URL.
- Supports graceful shutdown using `Ctrl+C`.
- Prints a notification when the server is stopped.

## Requirements

- Linux operating system.
- Bash.
- Python 3.
- `xdg-utils` for opening the application in the default browser.
- CineMemo Lite project with a working `server.py` file.

On Ubuntu, install the required system packages with:

```bash
sudo apt update
sudo apt install python3 xdg-utils
```

## Configuration

The script uses the following variables:

```bash
PROJECT_DIR="$HOME/Desktop/projects/javascript/cinememo-lite"
PORT=8888
URL="http://127.0.0.1:${PORT}/"
```

| Variable      | Description                                           |
| ------------- | ----------------------------------------------------- |
| `PROJECT_DIR` | Absolute path to the CineMemo Lite project directory. |
| `PORT`        | Local HTTP server port.                               |
| `URL`         | Local address opened in the default browser.          |

If your project is stored in a different directory, update `PROJECT_DIR` accordingly.

For example:

```bash
PROJECT_DIR="$HOME/Desktop/projects/javascript/cinememo-lite"
```

## Installation

1. Save the launcher script as `cinememo-lite`.
2. Make the script executable:

    ```bash
    chmod +x cinememo-lite
    ```

3. Copy it to a directory in your system's executable search path:

    ```bash
    sudo cp cinememo-lite /usr/local/bin/cinememo-lite
    ```

4. Verify that the script is available:

    ```bash
    command -v cinememo-lite
    ```

    Expected output:

    ```text
    /usr/local/bin/cinememo-lite
    ```

## Usage

Launch CineMemo Lite from any terminal:

```bash
cinememo-lite
```

The script will:

1. Verify that the project directory exists.
2. Change to the project directory.
3. Display the application URL.
4. Open the URL in the default browser.
5. Start the Python server.

Open the application manually if necessary:

[http://127.0.0.1:8888/](http://127.0.0.1:8888/)

To stop the server, press `Ctrl+C` in the terminal running the script.

## Troubleshooting

### Project directory not found

If the script reports that the CineMemo Lite directory cannot be found, verify the `PROJECT_DIR` value and make sure the directory exists.

### Port 8888 is already in use

If the server cannot start because port `8888` is occupied, identify the process using the port:

```bash
sudo ss -ltnp 'sport = :8888'
```

Stop the conflicting application if appropriate, or change the `PORT` value in the launcher script. Remember to update the URL if you change how it is constructed.

### Browser does not open automatically

Open the application manually at:

[http://127.0.0.1:8888/](http://127.0.0.1:8888/)

Make sure `xdg-utils` is installed and your default browser is configured correctly.

### Server does not start

Verify that Python 3 is installed:

```bash
python3 --version
```

Check that `server.py` exists in the CineMemo Lite project directory and that it can be executed with the selected Python interpreter.

## Notes

- The application runs locally on your computer.
- The server must remain running while you use the application.
- The launcher does not install project dependencies or modify application data.
- The launcher expects `server.py` to accept the port number as a command-line argument.

## License

Use, modify, and distribute this script freely.

# WebBridgeBot

WebBridgeBot is a Telegram bot designed to bridge the gap between Telegram media content and web browsers. By forwarding video, audio and photo files to WebBridgeBot, users can generate a web URL that hosts a webpage. This webpage, in turn, communicates with WebBridgeBot via WebSocket, allowing for instant playback of the media in a web browser. This seamless integration makes it easier than ever to enjoy Telegram media on various devices such as TVs, game consoles, and web kiosks.

## Features

- Real-time WebSocket communication.
- Download and stream audio and video files from Telegram chats directly.
- Access and play media files through a user-friendly web interface.
- Easy command access within Telegram to navigate to the web interface.
- Efficient file downloads and streaming, with partial content delivery support.

## Prerequisites

Before starting, ensure you have the following prerequisites installed:

- Docker
- Go (version 1.21 or newer as specified in the Dockerfile)
- Git
- CMake
- g++ (GNU C++ Compiler)
- Make
- zlib1g-dev (compression library)
- libssl-dev (SSL/TLS cryptography library)
- gperf (performance analyzer)

Additionally, you'll need:

- Telegram API credentials (API ID and API Hash)
- A Telegram Bot Token

## Setup Instructions

### Cloning the Repository

Begin by cloning the WebBridgeBot repository to your local machine:

```bash
git clone https://github.com/mshafiee/webbridgebot.git
cd webBridgeBot
```

### Building TDLib and OpenSSL

WebBridgeBot utilizes TDLib (Telegram Database Library) to interact with the Telegram API. The provided Makefile automates the process of cloning, building, and installing TDLib and OpenSSL, ensuring secure connections.

To prepare your environment, execute:

```bash
make all
```

This command will set up both TDLib and OpenSSL, placing the necessary files in `tdlib_install` and `openssl_install` directories, respectively.

### Building WebBridgeBot

After the dependencies are set up, build the WebBridgeBot application:

```bash
make webBridgeBot
```

This compiles the `webBridgeBot` Go application.

### Running WebBridgeBot with Docker

To build and run the WebBridgeBot Docker container, use the following commands:

```bash
docker build -t webbridgebot:latest .
docker run -p 8080:8080 \
-e "API_ID=your_api_id" \
-e "API_HASH=your_api_hash" \
-e "BOT_TOKEN=your_bot_token" \
-e "BASE_URL=http://example.com" \
webbridgebot:latest
```

Ensure to replace `your_api_id`, `your_api_hash`, and `your_bot_token` with your actual Telegram credentials. Adjust `http://example.com` to your WebBridgeBot instance's URL.

## Contributing

We welcome contributions to the WebBridgeBot project! Check out the issues tab for ways you can help make WebBridgeBot even better.

## License

WebBridgeBot is licensed under the GNU General Public License v3.0. See the [LICENSE](LICENSE) file for more details.

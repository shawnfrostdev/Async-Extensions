# DAB.YEET.SU Extension Repository

This repository contains music streaming extensions for the Async Music Player.

## Available Extensions

### DAB.YEET.SU Extension v1.0.2 ✅
- **High-Resolution Audio**: Support for up to 24bit/192kHz quality
- **Search Functionality**: Full-text search with pagination
- **Album Art**: Downloads cover art in multiple resolutions
- **Metadata**: Artist and album information retrieval
- **Configurable**: Quality preferences and search limits
- **Optimized**: Network optimization with proper timeouts
- **🎵 FIXED Streaming**: Now properly fetches stream URLs from Qobuz CDN

## Recent Fixes (v1.0.2)

### ✅ Stream URL Issue Resolution
- **Problem**: Extension was unable to get stream URLs, all endpoints returned 404 errors
- **Solution**: Discovered the correct API endpoint parameter format
- **Working Endpoint**: `GET /api/stream?trackId={id}` (note: `trackId` in camelCase)
- **Stream Source**: URLs are served from Qobuz's CDN via Akamaized

### API Investigation Results
Through extensive testing, we determined:
- The API requires exact parameter name: `trackId` (not `track_id`, `id`, or other variants)
- Only GET requests are supported for streaming (POST returns 405 Method Not Allowed)
- The API returns JSON with a `url` field containing the actual stream URL
- Stream URLs point to `streaming-qobuz-std.akamaized.net` with authentication tokens

## Installation

### Method 1: Repository URL
Add this repository to your Async Music Player:
```
https://shawnfrostdev.github.io/Async-Extensions/async-extension/manifest.json
```

### Method 2: Manual Installation
1. Download the APK from the `extensions/` directory
2. Install through Async Music Player's extension manager
3. Configure your preferred settings

## Repository Structure

```
async-extension/
├── manifest.json              # Repository manifest
├── extensions/               # Extension APK files
│   └── dabyeet-v1.0.2.apk    # DAB.YEET.SU extension (LATEST)
├── icons/                   # Extension icons
│   └── dabyeet.png          # DAB.YEET.SU icon (add manually)
└── README.md                # This file
```

## Extension Features

- **🎧 High-Res Audio**: Stream music up to 24bit/192kHz
- **🔍 Smart Search**: Fast search with pagination support
- **🖼️ Album Art**: Automatic cover art downloading
- **📊 Rich Metadata**: Complete track and artist information
- **⚙️ Configurable**: Customize quality and performance settings
- **🚀 Optimized**: Efficient networking with retry logic
- **✅ Working Streams**: Fixed stream URL fetching from Qobuz CDN

## Requirements

- Async Music Player (minimum version 1.0)
- Android 7.0+ (API level 24)
- Internet connection

## API Status

### ✅ Working Endpoints
- **Search**: `GET /api/search?q={query}&limit={limit}`
- **Stream**: `GET /api/stream?trackId={id}` ⭐ **FIXED**

### ❌ Non-Working Endpoints (Tested)
- `/api/stream/{id}` - Returns 404
- `/api/track/{id}/stream` - Returns 404
- `/api/play/{id}` - Returns 404
- Any POST requests to `/api/stream` - Returns 405

## Debugging Stream Issues

If you encounter stream URL issues:

1. Check that the track ID is correct (numeric)
2. Verify the API parameter is `trackId` (camelCase)
3. Ensure the request uses GET method
4. Check the JSON response contains a `url` field
5. Validate the returned URL is from a known CDN

Example working request:
```bash
curl "https://dab.yeet.su/api/stream?trackId=58452887"
```

## Changelog

### v1.0.2 (Latest) ✅
- **FIXED**: Stream URL fetching now works correctly
- **FIXED**: Corrected API parameter name from `track_id` to `trackId`
- **IMPROVED**: Better error handling and debugging
- **ADDED**: Comprehensive API endpoint testing
- **DOCUMENTED**: Correct API usage patterns

### v1.0.1
- Initial implementation with search functionality
- ❌ **Known Issue**: Stream URLs not working (fixed in v1.0.2)

## License

This extension is created for educational and personal use. Please respect the terms of service of DAB.YEET.SU.

## Support

For issues and support:
- Check the Async Music Player documentation
- Report bugs through the extension manager
- Contact the extension developer

## Disclaimer

This extension is not officially affiliated with DAB.YEET.SU. Users are responsible for complying with all applicable terms of service and copyright laws. 
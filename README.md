# BookWalker Auto-Pagination Script

A JavaScript automation script for the BookWalker manga downloader that automatically navigates through pages and saves them locally.

## Features

- **Automatic page detection** - Detects total manga pages automatically
- **Progress tracking** - Shows current page, percentage, and estimated time
- **Auto-stop** - Stops automatically when reaching the last page
- **Error handling** - Gracefully handles errors and connection issues
- **Progress reports** - Updates every 10 pages with elapsed time

## Prerequisites

Before using this script, you need:

1. **BookWalker Downloader Chrome** - The modified Chromium browser from the [Manga_downloader repository](https://github.com/xuzhengyi1995/Manga_downloader)
2. **Windows OS** - Currently only supports Windows
3. **Sufficient disk space** - Images are saved to `C:\bw_export_data\`

## Installation & Setup

### Step 1: Download the Modified Browser

1. Download `BW-downloader-chrome-bin.zip` from the repository
2. Extract the ZIP file to a folder on your computer
3. Create the output directory: `C:\bw_export_data\` (if it doesn't exist)

### Step 2: Launch the Browser

1. Open PowerShell or Command Prompt
2. Navigate to the extracted browser folder:
   ```cmd
   cd path\to\extracted\browser
   ```
3. Launch the browser with special flags:
   ```cmd
   .\chrome.exe --user-data-dir=c:\bw-downloader-profile --no-sandbox
   ```

### Step 3: Prepare the Manga

1. **Resize the browser window** - Make it small enough to display only ONE manga page
2. **Log in to BookWalker** - Use your account credentials
3. **Navigate to your manga** - Open the manga you want to download
4. **Reset reading progress** - Important: Reset the manga's reading status before opening it

## Using the Script

### Step 1: Open Developer Console

Press `F12` to open the browser's developer console

<img width="857" height="410" alt="{B5DEB31C-F6B9-4B8F-A307-F307BDF98686}" src="https://github.com/user-attachments/assets/05eb496f-9ae8-4350-b1fe-8a1690eaced2" />


### Step 2: Run the Script

Copy and paste the entire script into the console and press Enter

### Step 3: Monitor Progress

The script will automatically:
- Detect the total number of pages
- Calculate estimated download time
- Begin navigating through pages
- Save each page to `C:\bw_export_data\[UUID]\`
- Stop when complete

### What You'll See

```
Searching for BookWalker menu object...
✅ Menu object found in: L7v
Total pages: 186
Estimated time: 9.3 minutes
Starting automatic pagination...
=====================================
Page: 1/186 (1%)
Page: 2/186 (1%)
...
Progress: 10 pages in 0.5 minutes
...
✅ Download complete! Total: 186 pages
```

## Configuration

### Adjust Download Speed

Modify the `WAIT_TIME` variable at the top of the script:

```javascript
const WAIT_TIME = 3000; // Default: 3 seconds per page
```

- **Slow connection**: Increase to `5000` (5 seconds)
- **Fast connection**: Decrease to `2000` (2 seconds)
- **Very fast**: Try `1500` (1.5 seconds)

### Manual Controls

While the script is running, you can:

- **Stop the script**: Type `clearInterval(intervalo)` in the console
- **Check current page**: Type `pageIndex` in the console
- **Check total pages**: Type `totalPages` in the console

## Output Location

Downloaded manga pages are saved to:
```
C:\bw_export_data\
    └── [Random UUID folder]\
        ├── 0.jpg
        ├── 1.jpg
        ├── 2.jpg
        └── ...
```

## Troubleshooting

### Script stops after only a few pages

- **Cause**: Connection too fast for server
- **Solution**: Increase `WAIT_TIME` to 4000 or 5000

### No files in output folder

- **Cause**: Permission issues or folder doesn't exist
- **Solution**: 
  1. Create `C:\bw_export_data\` manually
  2. Ensure you have write permissions
  3. Launch browser with `--no-sandbox` flag

### "Menu object not found" error

- **Cause**: BookWalker updated their code structure
- **Solution**: Report the issue on the GitHub repository

### Images are incomplete or corrupted

- **Cause**: Page not fully loaded before capture
- **Solution**: Increase `WAIT_TIME` to allow full page load

### Browser crashes or freezes

- **Cause**: Memory issues with large manga
- **Solution**: 
  1. Close other programs
  2. Download in smaller batches
  3. Restart browser between manga

## Tips for Best Results

1. **Stable internet connection** - Avoid downloads on unstable WiFi
2. **Don't minimize browser** - Keep the browser window visible
3. **One manga at a time** - Complete one before starting another
4. **Check first few pages** - Verify images are saving correctly before leaving unattended
5. **Morning/late night** - Download during off-peak hours for better speeds

## Important Notes

- This tool is for personal backup of legally purchased manga only
- Respect copyright and publisher terms of service
- Do not distribute downloaded content
- The browser is modified for downloading only - do not use for regular browsing
- ![risitas-laugh](https://github.com/user-attachments/assets/90a84a91-04be-4ba2-9570-24d1457388c9)


## Need Help?

If you encounter issues not covered here:

1. Check the [original repository issues](https://github.com/xuzhengyi1995/Manga_downloader/issues)
2. Ensure you're using the latest version of the downloader
3. Try the script with a free/sample manga first to test your setup

## Script Version

Version: 1.0
Last Updated: August 2025
Compatible with: BookWalker Japan & Taiwan

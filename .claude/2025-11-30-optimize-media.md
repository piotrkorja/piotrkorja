DELIVERABLE:
============
Script Location: /tmp/organize_media.sh

HOW TO RUN:
===========
Simply execute in your terminal:
    /tmp/organize_media.sh

You'll be prompted for your sudo password (required because the files are owned by user "piotr").

WHAT IT DOES:
=============
1. Finds all media files recursively in /Users/Shared/SharedGoogleDrive
2. Organizes them into ~/media/YYYY-qN/ folders based on creation date
   Examples:
   - ~/media/2023-q1/
   - ~/media/2023-q2/
   - ~/media/2024-q3/
   etc.

3. Flattens directory structure (no folder paths preserved)
4. Handles duplicate filenames automatically (adds _1, _2, etc.)
5. Changes file ownership to your user account
6. Shows progress as files are moved

SUPPORTED FORMATS:
==================
Images: jpg, jpeg, png, gif, heic, heif, webp, bmp, tiff, tif, raw, cr2, nef, arw, dng
Videos: mp4, mov, avi, mkv, m4v, mpg, mpeg, wmv, flv, webm, 3gp, mts, m2ts

CONTEXT:
========
- Current directory: /Users/Shared/SharedGoogleDrive
- Target directory: ~/media (will be created if it doesn't exist)
- Permission issue: Files owned by UID 502 (piotr), running as UID 501 (piotrkorj)
- Solution: Script uses sudo to access and move files
- Goal: Prepare files for Google Photos upload

TECHNICAL DETAILS:
==================
- Uses file birth date (creation date) on macOS
- Falls back to modification date if birth date unavailable
- Quarters: Q1 (Jan-Mar), Q2 (Apr-Jun), Q3 (Jul-Sep), Q4 (Oct-Dec)
- Script includes error handling and progress reporting

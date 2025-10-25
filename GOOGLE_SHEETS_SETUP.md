# Hall Seat Management System - Google Sheets Integration Guide

## Overview
This guide will help you set up Google Sheets integration to allow collaborative editing of your hall seat data from anywhere in the world.

## Prerequisites
- A Google account
- Access to Google Cloud Console
- Basic understanding of API configuration

## Step-by-Step Setup

### 1. Create Google Cloud Project

1. **Open Google Cloud Console**
   - Go to [https://console.cloud.google.com/](https://console.cloud.google.com/)
   - Sign in with your Google account

2. **Create New Project**
   - Click "Select a project" dropdown
   - Click "New Project"
   - Enter project name: "Hall Seat Management"
   - Click "Create"

3. **Enable Google Sheets API**
   - Go to "APIs & Services" > "Library"
   - Search for "Google Sheets API"
   - Click on it and click "Enable"

### 2. Create API Credentials

1. **Create API Key**
   - Go to "APIs & Services" > "Credentials"
   - Click "Create Credentials" > "API Key"
   - Copy your API key and save it securely
   - Click "Restrict Key" to configure restrictions

2. **Restrict API Key (Recommended)**
   - Under "API restrictions": Select "Restrict key"
   - Choose "Google Sheets API"
   - Under "Website restrictions": Add your domain
   - Click "Save"

### 3. Create Google Sheets Document

1. **Create New Spreadsheet**
   - Go to [https://sheets.google.com/](https://sheets.google.com/)
   - Click "Blank" to create new spreadsheet
   - Name it "Hall Seat Allocation 2025"

2. **Set Up Column Headers** (Row 1)
   ```
   A1: Seat ID
   B1: Student Name  
   C1: Department
   D1: Session
   E1: Room No
   F1: Building
   G1: Floor No
   H1: Floor Teacher
   I1: Status
   ```

3. **Add Sample Data** (Starting from Row 2)
   ```
   A2: J-10007(A)  B2: Ahmed Hassan     C2: CSE       D2: 2023-24
   E2: 10007       F2: Jamuna Building  G2: 1st Floor H2: Dr. Rahman  I2: Current
   ```

4. **Share the Spreadsheet**
   - Click "Share" button (top right)
   - Under "General access": Select "Anyone with the link"
   - Set permission to "Viewer" (for read-only API access)
   - Copy the sharing link

5. **Get Spreadsheet ID**
   - From the URL: `https://docs.google.com/spreadsheets/d/SPREADSHEET_ID/edit`
   - Copy the SPREADSHEET_ID part
   - Example: `1BxiMVs0XRA5nFMdKvBdBZjgmUUqptlbs74OgvE2upms`

### 4. Configure the Application

1. **Open index.html**
   - Find the `GOOGLE_SHEETS_CONFIG` object (around line 560)
   
2. **Update Configuration**
   ```javascript
   const GOOGLE_SHEETS_CONFIG = {
       apiKey: 'YOUR_API_KEY_HERE',           // Replace with your API key
       spreadsheetId: 'YOUR_SPREADSHEET_ID', // Replace with your spreadsheet ID  
       range: 'Sheet1!A:I',                  // Keep as is unless you change sheet name
       enabled: true                          // Change from false to true
   };
   ```

3. **Save the File**
   - Save index.html with your changes

### 5. Test the Integration

1. **Open the Application**
   - Open index.html in your browser
   - You should see a notification if Google Sheets integration is working

2. **Verify Data Loading**
   - The app should automatically load data from your Google Sheets
   - Check browser console for any errors

3. **Test Real-time Updates**
   - Edit data in Google Sheets
   - Click "Refresh Data" button in the app
   - Changes should appear within 5 minutes automatically

## Data Format Guidelines

### Required Columns
Make sure your Google Sheets has these exact column headers:

| Column | Required | Format | Example |
|--------|----------|--------|---------|
| Seat ID | Yes | Building-Room(Letter) | J-10007(A) |
| Student Name | Yes | Text | Ahmed Hassan |
| Department | Yes | Text | CSE |
| Session | Yes | YYYY-YY | 2023-24 |
| Room No | Yes | Number | 10007 |
| Building | Yes | Text | Jamuna Building |
| Floor No | No | Text | 1st Floor |
| Floor Teacher | No | Text | Dr. Rahman |
| Status | Yes | Current/Expired | Current |

### Building Codes
- **J** = Jamuna Building
- **P** = Padma Building  
- **M** = Meghna Building

### Sample Data Template
Use the provided `sample-data-template.csv` file to populate your Google Sheets quickly.

## Security Best Practices

### API Key Security
1. **Restrict by Website**
   - Add your domain to API key restrictions
   - Never share your API key publicly

2. **Monitor Usage**
   - Check Google Cloud Console for API usage
   - Set up billing alerts if needed

3. **Regular Rotation**
   - Rotate API keys every 6 months
   - Update the application configuration when rotating

### Spreadsheet Permissions
1. **Read-Only Access**
   - Set spreadsheet to "Viewer" for API access
   - Only give "Editor" access to trusted administrators

2. **Share Carefully**
   - Don't make spreadsheet publicly editable
   - Use specific email addresses for editor access

## Troubleshooting

### Common Issues

1. **API Key Not Working**
   - Check if Google Sheets API is enabled
   - Verify API key restrictions
   - Make sure key is copied correctly

2. **No Data Loading**
   - Verify spreadsheet ID is correct
   - Check if spreadsheet is shared publicly
   - Ensure column headers match exactly

3. **Permission Denied**
   - Check spreadsheet sharing settings
   - Verify API key has proper permissions
   - Make sure spreadsheet is not private

4. **CORS Errors**
   - Add your domain to API key restrictions
   - Serve the application from a web server (not file://)

### Debug Steps
1. Open browser developer tools (F12)
2. Check Console tab for error messages
3. Look for network requests to Google Sheets API
4. Verify the API response in Network tab

## Advanced Configuration

### Custom Column Mapping
If your spreadsheet uses different column names, update the `columnMapping` object in the code:

```javascript
const columnMapping = {
    'seat_id': ['seat id', 'seatid', 'id'],
    'name': ['student name', 'name', 'full name'],
    // Add your custom column names here
};
```

### Automatic Sync Interval
Change the sync frequency by modifying this line:
```javascript
setInterval(checkForGoogleSheetsUpdates, 5 * 60 * 1000); // 5 minutes
```

### Multiple Sheets Support
To read from multiple sheets, modify the range:
```javascript
range: 'Students!A:I'  // Read from 'Students' sheet instead of 'Sheet1'
```

## Support

### Getting Help
1. Check browser console for detailed error messages
2. Verify Google Cloud Console for API usage and errors
3. Test with a simple spreadsheet first
4. Review Google Sheets API documentation

### Resources
- [Google Sheets API Documentation](https://developers.google.com/sheets/api)
- [Google Cloud Console](https://console.cloud.google.com/)
- [API Key Best Practices](https://cloud.google.com/docs/authentication/api-keys)

### Contact
For technical support with this integration, please check the GitHub repository issues section.

---

**Last Updated**: October 2025  
**Version**: 1.0
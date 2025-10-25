# Hall Seat Management System

A modern, web-based hall seat allocation management system for Bijoy Ekattor Hall, University of Dhaka. This system allows administrators to track student seat allocations with real-time status updates and integrates with Google Sheets for collaborative data management.

## 🌐 Live Demo

Visit the live application: **[https://shaharia223.github.io/PolitixPlume/](https://shaharia223.github.io/PolitixPlume/)**

## ✨ Features

### 🏠 Hall Management
- **Multi-Building Support**: Manage seats across Jamuna, Padma, and Meghna buildings
- **Real-time Status Tracking**: Monitor current and expired seat allocations
- **Visual Dashboard**: Interactive grid display with color-coded status indicators
- **Advanced Filtering**: Filter by building, room, floor, or allocation status
- **Smart Search**: Search by seat ID, student name, or department

### � Data Management
- **Google Sheets Integration**: Connect to Google Drive spreadsheets for real-time collaboration
- **Offline Support**: Works completely offline with local data storage
- **Excel Import/Export**: Support for .xlsx, .xls, and .csv files
- **Data Backup**: JSON backup and restore functionality
- **Merge/Replace Options**: Choose how to handle data updates

### 🔐 Security & Access
- **Admin Authentication**: Secure admin panel with session management
- **Public Viewing**: Anyone can view seat allocations without login
- **Collaborative Editing**: Multiple users can edit Google Sheets simultaneously
- **Data Validation**: Preview changes before applying updates

## 🚀 Quick Start

### Option 1: Use Live Version (Recommended)
1. Visit [https://shaharia223.github.io/PolitixPlume/](https://shaharia223.github.io/PolitixPlume/)
2. The system will automatically load sample data
3. Click "Administrator Login" to access admin features (see credentials below)

### Option 2: Host Your Own Copy
1. Fork this repository
2. Enable GitHub Pages in your repository settings
3. Your site will be available at `https://yourusername.github.io/repositoryname/`

## 📋 Google Sheets Integration Setup

### Step 1: Create Google Sheets API Project
1. Go to [Google Cloud Console](https://console.cloud.google.com/)
2. Create a new project or select existing one
3. Enable the Google Sheets API
4. Create credentials (API Key for public access or Service Account for enhanced security)

### Step 2: Set Up Your Spreadsheet
1. Create a new Google Sheets document
2. Set up columns as shown in the template below
3. Share the spreadsheet (view access for public, edit access for authorized users)
4. Get the spreadsheet ID from the URL

### Step 3: Configure the Application
1. Update the Google Sheets configuration in the code:
```javascript
// Replace with your Google Sheets details
const GOOGLE_SHEETS_CONFIG = {
    apiKey: 'YOUR_API_KEY',
    spreadsheetId: 'YOUR_SPREADSHEET_ID',
    range: 'Sheet1!A:I'
};
```

## 📊 Data Format

Your Google Sheets document should have these columns:

| Column A | Column B | Column C | Column D | Column E | Column F | Column G | Column H | Column I |
|----------|----------|----------|----------|----------|----------|----------|----------|----------|
| Seat ID | Student Name | Department | Session | Room No | Building | Floor No | Floor Teacher | Status |
| J-10007(A) | Ahmed Hassan | CSE | 2023-24 | 10007 | Jamuna Building | 1st Floor | Dr. Rahman | Current |
| P-20001(B) | Fatima Khan | EEE | 2022-23 | 20001 | Padma Building | 2nd Floor | Prof. Ahmed | Expired |

### Seat ID Format
```
[Building Code]-[Room Number]([Seat Letter])

Examples:
- J-10007(A) = Jamuna Building, Room 10007, Seat A
- P-20001(B) = Padma Building, Room 20001, Seat B
- M-30005(C) = Meghna Building, Room 30005, Seat C
```

## 🔑 Default Admin Credentials

For demo purposes, use these credentials to access admin features:
- **Username**: `admin` | **Password**: `hall2025`
- **Username**: `hallmanager` | **Password**: `manager123`
- **Username**: `supervisor` | **Password**: `super456`

**⚠️ Important**: Change these credentials before production use!

## 🛠️ Local Development

1. Clone the repository:
```bash
git clone https://github.com/Shaharia223/PolitixPlume.git
cd PolitixPlume
```

2. Open `index.html` in your browser or serve it locally:
```bash
# Using Python
python -m http.server 8000

# Using Node.js
npx serve .

# Using PHP
php -S localhost:8000
```

## 🌐 Deployment Options

### GitHub Pages (Free)
1. Fork this repository
2. Go to Settings → Pages
3. Select "Deploy from a branch"
4. Choose "main" branch and "/ (root)"
5. Your site will be live at `https://yourusername.github.io/repositoryname/`

### Netlify (Free)
1. Connect your GitHub repository to Netlify
2. Set build settings to publish the root directory
3. Deploy automatically on every push

### Vercel (Free)
1. Import your GitHub repository to Vercel
2. Deploy with default settings
3. Get automatic deployments and preview links

## 📱 Browser Compatibility

- ✅ Chrome 60+
- ✅ Firefox 55+
- ✅ Safari 12+
- ✅ Edge 79+
- ✅ Mobile browsers (iOS Safari, Chrome Mobile)

## 🎨 Customization

### Modify Building Configuration
Update the building codes in your data source:
- `J` for Jamuna Building
- `P` for Padma Building  
- `M` for Meghna Building

### Change Color Scheme
Modify CSS variables in `index.html`:
```css
:root {
    --current-color: #10b981;  /* Green for current seats */
    --expired-color: #ef4444;  /* Red for expired seats */
    --background-opacity: 0.95; /* Background transparency */
}
```

### Update Admin Credentials
Find and modify the `ADMIN_CREDENTIALS` object in the JavaScript code:
```javascript
const ADMIN_CREDENTIALS = {
    'youradmin': 'yourpassword',
    'manager': 'managerpass'
};
```

## 🔧 Google Sheets API Integration Details

### Public Read Access (Recommended for viewing)
```javascript
// Simple API key setup for read-only access
const API_KEY = 'YOUR_GOOGLE_API_KEY';
const SHEET_ID = 'YOUR_SPREADSHEET_ID';
const RANGE = 'Sheet1!A:I';

const url = `https://sheets.googleapis.com/v4/spreadsheets/${SHEET_ID}/values/${RANGE}?key=${API_KEY}`;
```

### Service Account (For write access)
```javascript
// For applications that need to write data
const SERVICE_ACCOUNT_EMAIL = 'your-service-account@project.iam.gserviceaccount.com';
// Include service account key configuration
```

## � Performance Features

- **Lazy Loading**: Large datasets load progressively
- **Smart Pagination**: Automatic pagination for 100+ seats
- **Debounced Search**: Optimized search with 300ms debounce
- **Local Caching**: Data cached in browser for faster access
- **Responsive Design**: Optimized for all screen sizes

## �️ Security Considerations

- Google Sheets data is cached locally for performance
- Admin sessions expire after 2 hours of inactivity
- No sensitive data is stored in localStorage
- API keys should be restricted to specific domains
- Consider using environment variables for production

## 📞 Support & Contributing

### Issues & Bugs
Please report issues through GitHub Issues with:
- Browser version and OS
- Steps to reproduce the problem
- Screenshots if applicable

### Contributing
1. Fork the repository
2. Create a feature branch
3. Make your changes
4. Test thoroughly
5. Submit a pull request

## 📄 License

This project is open source and available under the MIT License.

## 🏛️ About Bijoy Ekattor Hall

Bijoy Ekattor Hall is a residential hall of the University of Dhaka, Bangladesh. This system is designed to help hall administrators efficiently manage student seat allocations across multiple buildings while maintaining transparency and accessibility.

---

**Built with ❤️ for Bijoy Ekattor Hall, University of Dhaka**

For technical support or feature requests, please open an issue on GitHub.
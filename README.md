# વિહાર રક્ષા તપ - Web Application 🙏

A complete full-stack web application for managing વિહાર રક્ષા તપ (Vihar Raksha Tap) form submissions with **Excel-based storage** and **Gujarati language support**.

## 🎯 Features

- ✅ Beautiful home page with image carousel
- ✅ Informative about page with tap details
- ✅ Form submission with Gujarati language support
- ✅ Excel file-based data storage (no database required)
- ✅ Automatic backup system
- ✅ File locking for concurrent access
- ✅ Admin dashboard for managing submissions
- ✅ Export functionality
- ✅ Email notifications (optional)
- ✅ Responsive design matching Tally style
- ✅ Real-time validation

## 🛠️ Technology Stack

### Backend
- Node.js + Express.js
- ExcelJS (Excel file manipulation)
- JWT Authentication
- Nodemailer (Email)
- File locking (proper-lockfile)

### Frontend
- React 18
- React Router v6
- React Slick (Carousel)
- Axios
- React Toastify
- Gujarati Font (Noto Sans Gujarati)

## 📦 Installation

### Prerequisites
- Node.js v18 or higher
- npm or yarn

### Step 1: Backend Setup

```bash
# Navigate to backend directory
cd app/backend

# Install dependencies (already done)
npm install

# The Excel file is already initialized!
```

### Step 2: Frontend Setup

```bash
# Navigate to frontend directory
cd app/frontend

# Install dependencies (already done)
npm install
```

## 🚀 Running the Application

### Start Backend Server

```bash
# From app/backend directory
cd app/backend
npm run dev
```

The backend will start at: **http://localhost:5000**

### Start Frontend Application

```bash
# Open a new terminal
# From app/frontend directory
cd app/frontend
npm start
```

The frontend will start at: **http://localhost:3000**

## 📱 Application Flow

### **Navigation Journey:**

1. **Home Page** (`http://localhost:3000`)
   - Image carousel with 4 slides
   - Complete content about વિહાર રક્ષા તપ
   - "આગળ વધો (Next)" button

2. **About Page** (`http://localhost:3000/about`)
   - Another image carousel
   - Details about the tap
   - Benefits and important information
   - "ફોર્મ ભરો (Fill the Form)" button

3. **Form Page** (`http://localhost:3000/form`)
   - Back button to return to About page
   - Form with Gujarati fields
   - Submit button
   - Admin login link at bottom

4. **Thank You Page** (`http://localhost:3000/thank-you`)
   - Success message with Submission ID
   - Option to submit another form

5. **Admin Panel** (`http://localhost:3000/admin/login`)
   - Login page → Dashboard
   - Manage all submissions

## 📝 Using the Application

### Public User Journey

1. **Visit Home Page** - Read about વિહાર રક્ષા તપ
2. **Click Next** - Go to About page
3. **Read Details** - Learn about the tap
4. **Click "ફોર્મ ભરો"** - Navigate to form
5. **Fill Form** with required details:
   - **નામ (Name)** - Required
   - **મોબાઇલ (Mobile)** - Required (10 digits)
   - **ઈમેલ (Email)** - Optional
   - Other optional fields
6. **Submit** - Get confirmation with Submission ID

### Admin Dashboard

**Login:** `http://localhost:3000/admin/login`

**Credentials:**
- Username: `admin`
- Password: `admin123`

**Features:**
- View all submissions
- Search by name, mobile, email, city
- Update submission status
- Delete submissions
- Export to Excel
- View statistics

## 🎨 Page Features

### Home Page
- **4-Image Carousel** with auto-play
- Complete Gujarati content about વિહાર રક્ષા તપ
- Beautiful gradient design
- Smooth navigation
- Responsive layout

### About Page
- **4-Image Carousel** with different images
- Detailed information cards:
  - તપનો હેતુ (Purpose)
  - તપનો સમય (Timing)
  - તપના લાભો (Benefits)
  - મહત્વપૂર્ણ નોંધ (Important Note)
- Call-to-action button
- Back button to home page

### Form Page
- **Back button** to About page
- Clean, Tally-inspired design
- Real-time validation
- Gujarati + English labels
- Admin link at bottom

## 📊 API Endpoints

### Public Endpoints

#### Submit Form
```http
POST /api/submissions
Content-Type: application/json

{
  "name": "String",
  "mobile": "String",
  "email": "String",
  "address": "String",
  "city": "String",
  "state": "String",
  "remarks": "String"
}
```

### Admin Endpoints (Requires Authentication)

#### Login
```http
POST /api/admin/login
Content-Type: application/json

{
  "username": "admin",
  "password": "admin123"
}
```

#### Get All Submissions
```http
GET /api/submissions?page=1&limit=20&status=pending
Authorization: Bearer {token}
```

#### Get Statistics
```http
GET /api/submissions/stats
Authorization: Bearer {token}
```

#### Search, Export, Update, Delete
- `GET /api/submissions/search?q=query`
- `GET /api/submissions/export`
- `PUT /api/submissions/:id`
- `DELETE /api/submissions/:id`

## 📁 Excel File Structure

Location: `app/backend/data/submissions.xlsx`

### Sheet 1: "Submissions"

| Column | Header (Gujarati) | Description |
|--------|-------------------|-------------|
| A | ID | Unique submission ID |
| B | તારીખ (Date) | Submission timestamp |
| C | નામ (Name) | Full name |
| D | મોબાઇલ (Mobile) | Mobile number |
| E | ઈમેલ (Email) | Email address |
| F | સરનામું (Address) | Full address |
| G | શહેર (City) | City name |
| H | રાજ્ય (State) | State name |
| I | સ્થિતિ (Status) | pending/reviewed/archived |
| J | IP Address | Submitter's IP |
| K | Remarks | Additional notes |

## 💾 Backup System

- **Automatic Backups:** Daily at 2:00 AM
- **Manual Backup:** Created before each write operation
- **Location:** `app/backend/data/backups/`
- **Retention:** Last 30 backups

## 🎨 Carousel Images

Currently using **placeholder images** from `placeholder.com`.

### To Add Your Own Images:

**Option 1: Update URLs in code**
```javascript
// In HomePage.jsx and AboutPage.jsx
const carouselImages = [
  {
    url: '/images/slide1.jpg',  // Your image path
    alt: 'Description'
  },
  // ... more images
];
```

**Option 2: Add images to public folder**
1. Create `app/frontend/public/images/` folder
2. Add your images (slide1.jpg, slide2.jpg, etc.)
3. Update URLs to: `/images/slide1.jpg`

## 📝 Customization

### Change Carousel Speed
```javascript
// In HomePage.jsx or AboutPage.jsx
const carouselSettings = {
  autoplaySpeed: 3000,  // Change to desired milliseconds
  // ...
};
```

### Change Colors
Edit `app/frontend/src/index.css`:
```css
:root {
  --primary-color: #667eea;  /* Change this */
  --primary-dark: #5568d3;   /* And this */
}
```

### Update Admin Credentials
Edit `app/backend/.env`:
```env
ADMIN_USERNAME=your_username
ADMIN_PASSWORD=your_password
```

## 🐛 Troubleshooting

### Carousel not working
- Make sure `react-slick` is installed
- Check browser console for errors
- Import CSS files are present

### Images not showing
- Check image URLs are correct
- Verify internet connection (for placeholder images)
- Check browser console for 404 errors

### Navigation not working
- Verify all routes are defined in `App.js`
- Check React Router is installed
- Clear browser cache

## 📚 Project Structure

```
app/
├── backend/
│   ├── data/
│   │   ├── submissions.xlsx
│   │   ├── backups/
│   │   └── exports/
│   └── src/
│       ├── config/
│       ├── controllers/
│       ├── middleware/
│       ├── routes/
│       ├── services/
│       └── server.js
│
└── frontend/
    ├── public/
    │   └── index.html (with Gujarati font)
    └── src/
        ├── components/
        │   └── Form/
        │       ├── FormContainer.jsx
        │       └── FormContainer.css
        ├── pages/
        │   ├── HomePage.jsx & .css
        │   ├── AboutPage.jsx & .css
        │   ├── ThankYouPage.jsx & .css
        │   ├── AdminLoginPage.jsx & .css
        │   └── AdminDashboard.jsx & .css
        ├── utils/
        │   └── api.js
        ├── App.js
        └── index.css
```

## 🚀 Deployment

### Backend (VPS/DigitalOcean)
1. Setup Node.js on server
2. Copy backend files
3. Configure `.env` for production
4. Use PM2: `pm2 start src/server.js`

### Frontend (Vercel/Netlify)
1. Build: `npm run build`
2. Deploy `build` folder
3. Set environment variable: `REACT_APP_API_URL`

## 📞 Support

For issues or questions:
- Check browser console (F12)
- Check backend terminal output
- Verify both servers are running
- Check `.env` configuration

## ⚙️ Configuration Files

### Backend `.env`
```env
NODE_ENV=development
PORT=5000
ADMIN_USERNAME=admin
ADMIN_PASSWORD=admin123
CLIENT_URL=http://localhost:3000
```

### Frontend `.env`
```env
REACT_APP_API_URL=http://localhost:5000/api
REACT_APP_ENV=development
```

## 📄 License

Proprietary software for વિહાર રક્ષા તપ management.

---

**જય જિનેન્દ્ર! 🙏**

**Created with Claude Code by Anthropic**

---

## 🆕 Recent Updates

### New Navigation Flow (Current Version)
- ✅ Added Home Page with carousel
- ✅ Added About Page with details
- ✅ Added back buttons for navigation
- ✅ Improved user journey
- ✅ Better content presentation
- ✅ Enhanced mobile responsiveness

### Navigation Path
```
Home → About → Form → Thank You
  ↓      ↓       ↓
[Next] [Fill] [Back]
         ↓
    Admin Login
         ↓
    Dashboard
```

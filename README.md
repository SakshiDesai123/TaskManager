
# 📋 Task Manager - Supabase Backend

A modern, responsive task management web application with real-time cloud storage using Supabase.

![Task Manager Screenshot](https://img.shields.io/badge/Status-Active-success) ![License](https://img.shields.io/badge/License-MIT-blue) ![Supabase](https://img.shields.io/badge/Backend-Supabase-green)

## ✨ Features

- **🔐 Cloud Storage** - Tasks stored securely in Supabase PostgreSQL database
- **📱 Responsive Design** - Works on desktop, tablet, and mobile
- **⚡ Real-time Operations** - Instant CRUD operations with Supabase
- **🎯 Priority System** - Low, Medium, High priority classification
- **🔍 Smart Search** - Search tasks by title or description
- **📊 Task Statistics** - Real-time task count and database status
- **🎨 Modern UI** - Gradient design with smooth animations

## 🚀 Live Demo

[Click here to try the live demo](#) • [View Source Code](#)

## 📸 Screenshots

| Tasks View | Add Task | Configuration |
|------------|----------|---------------|
| ![Tasks](/test/taskview.png) | ![Add](/tes/addtask.png) | ![Config](/test/config.jpg) |

## 🛠️ Technologies Used

- **Frontend**: HTML5, CSS3, Vanilla JavaScript
- **Backend**: [Supabase](https://supabase.com) (PostgreSQL + REST API)
- **Icons**: Font Awesome 6.4.0
- **Styling**: Custom CSS with Flexbox/Grid
- **Deployment**: Single-file deployment ready

## ⚡ Quick Start

### Option 1: Use Pre-configured Version
1. Download `index.html`
2. Open in any modern browser
3. It's already configured with demo credentials!

### Option 2: Setup with Your Own Supabase

#### Step 1: Clone and Setup
```bash
# Clone or download the repository
git clone <repository-url>
cd task-manager-supabase

# The project is a single HTML file
# No build process or dependencies needed!
```

#### Step 2: Create Supabase Project
1. Go to [supabase.com](https://supabase.com) and sign up
2. Create a new project
3. Wait for database to initialize (2-3 minutes)
4. Navigate to Project Settings → API
5. Copy:
   - Project URL
   - `anon` public key

#### Step 3: Database Setup
In Supabase SQL Editor, run:
```sql
-- Create tasks table
CREATE TABLE IF NOT EXISTS tasks (
  id BIGSERIAL PRIMARY KEY,
  title TEXT NOT NULL,
  description TEXT,
  priority TEXT DEFAULT 'medium',
  completed BOOLEAN DEFAULT FALSE,
  created_at TIMESTAMP DEFAULT NOW()
);

-- Enable Row Level Security
ALTER TABLE tasks ENABLE ROW LEVEL SECURITY;

-- Create policy for public access (for demo)
CREATE POLICY "Enable public access" ON tasks
  FOR ALL USING (true);
```

#### Step 4: Configure Application
1. Open `index.html` in a text editor
2. Navigate to Configuration section
3. Enter your Supabase credentials:
   - **Supabase URL**: Your project URL
   - **API Key**: `anon` public key
4. Save and open in browser

## 📁 Project Structure

```
task-manager/
│
├── index.html                 # Main application file
│
├── (Virtual Structure - All in one file)
│   ├── HTML Structure
│   │   ├── Header with connection status
│   │   ├── Sidebar navigation
│   │   ├── Main content sections
│   │   └── Footer
│   │
│   ├── CSS Styles
│   │   ├── Responsive layout
│   │   ├── Gradient designs
│   │   ├── Task cards styling
│   │   └── Interactive elements
│   │
│   └── JavaScript Functions
│       ├── supabase-client.js
│       ├── task-operations.js
│       ├── ui-manager.js
│       └── config-manager.js
│
└── README.md                 # This file
```

## 🔧 Configuration

### Environment Variables (LocalStorage)
The app stores configuration in browser's localStorage:
- `supabaseUrl`: Your Supabase project URL
- `supabaseKey`: Your anon public key

### Default Configuration
```javascript
// Default demo credentials (replace with your own)
supabaseUrl: 'https://eoriotzlopgusgtnkult.supabase.co'
supabaseKey: 'eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9...'
```

## 🎮 Usage Guide

### Adding Tasks
1. Click "Add New Task" in sidebar
2. Fill in:
   - **Title**: Task name (required)
   - **Priority**: Low/Medium/High
   - **Description**: Optional details
3. Click "Save Task"

### Managing Tasks
- **Mark Complete**: Click "Mark Complete" button
- **Delete Task**: Click red "Delete" button
- **Search**: Use search bar to find tasks
- **Refresh**: Click refresh button in All Tasks

### Sections Overview
- **All Tasks**: View all tasks with completion status
- **Add New Task**: Create new tasks
- **Search Tasks**: Search by keywords
- **Configuration**: Setup Supabase credentials

## 🔌 API Endpoints

The app uses these Supabase endpoints:

| Method | Endpoint | Description |
|--------|----------|-------------|
| GET | `/tasks` | Fetch all tasks |
| POST | `/tasks` | Create new task |
| PATCH | `/tasks?id=eq.{id}` | Update task |
| DELETE | `/tasks?id=eq.{id}` | Delete task |

## 📱 Responsive Breakpoints

```css
/* Desktop: > 768px */
.tasks-grid { grid-template-columns: repeat(3, 1fr); }

/* Tablet: 480px - 768px */
@media (max-width: 768px) { ... }

/* Mobile: < 480px */
@media (max-width: 480px) { ... }
```

## 🧪 Testing

### Add Sample Data
Open browser console and run:
```javascript
addSampleData(); // Adds 5 sample tasks
```

### Test Connection
Use the "Test Connection" button in Configuration section.

## 🐛 Troubleshooting

| Issue | Solution |
|-------|----------|
| Connection failed | Check Supabase URL and API key |
| Tasks not loading | Verify database table exists |
| CORS errors | Enable CORS in Supabase dashboard |
| Actions not working | Clear browser cache and localStorage |

### Common Errors

1. **"Failed to fetch"**
   - Check internet connection
   - Verify Supabase URL is correct

2. **"JWT expired"**
   - Regenerate API keys in Supabase
   - Update configuration

3. **"RLS policy violation"**
   - Ensure RLS policy allows public access (for demo)
   - Check table permissions

## 🔒 Security Notes

⚠️ **Important Security Considerations:**

1. **Production Use**: Replace demo credentials with your own
2. **Row Level Security**: Customize RLS policies for production
3. **API Keys**: Use environment variables in production
4. **Authentication**: Add user authentication for multi-user apps

### Recommended Production Setup
```javascript
// For production, use environment variables
supabaseUrl: process.env.SUPABASE_URL
supabaseKey: process.env.SUPABASE_ANON_KEY
```

## 🌟 Features in Detail

### Task Management
- Create, read, update, delete tasks
- Mark tasks as complete/incomplete
- Priority-based organization
- Created timestamp tracking

### User Interface
- Smooth animations and transitions
- Color-coded priority indicators
- Connection status indicator
- Success/error notifications

### Database Features
- PostgreSQL backend
- Real-time synchronization
- Automatic timestamps
- Secure API access

## 📄 License

MIT License - See [LICENSE](LICENSE) file for details.

## 👨‍💻 Author

**Sakshi Desai**
- GitHub: [@yourusername](https://github.com/yourusername)
- Email: your.email@example.com

## 🙏 Acknowledgments

- [Supabase](https://supabase.com) for the amazing backend service
- [Font Awesome](https://fontawesome.com) for icons
- Contributors and testers

## 🤝 Contributing

1. Fork the repository
2. Create a feature branch (`git checkout -b feature/AmazingFeature`)
3. Commit changes (`git commit -m 'Add AmazingFeature'`)
4. Push to branch (`git push origin feature/AmazingFeature`)
5. Open a Pull Request

## 📞 Support

For support, please:
1. Check the [Troubleshooting](#troubleshooting) section
2. Open an issue on GitHub
3. Email: support@example.com

---

<div align="center">

### ⭐ Star this repo if you found it helpful!

**Built with ❤️ using Supabase**

[![Supabase](https://img.shields.io/badge/Supabase-3ECF8E?style=for-the-badge&logo=supabase&logoColor=white)](https://supabase.com)
[![HTML5](https://img.shields.io/badge/HTML5-E34F26?style=for-the-badge&logo=html5&logoColor=white)](https://developer.mozilla.org/en-US/docs/Web/HTML)
[![JavaScript](https://img.shields.io/badge/JavaScript-F7DF1E?style=for-the-badge&logo=javascript&logoColor=black)](https://developer.mozilla.org/en-US/docs/Web/JavaScript)

</div>

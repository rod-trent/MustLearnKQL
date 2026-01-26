# 🔍 Must Learn KQL Learning Hub

An interactive, AI-powered companion application for learning **Kusto Query Language (KQL)** based on the "Must Learn KQL" series by Rod Trent.

## ✨ Features

### 🎓 Interactive Learning Modules
- Structured learning path from beginner to advanced
- Hands-on exercises and practice queries
- Real-time query execution against demo or live Kusto clusters
- Progress tracking with points and badges

### 🤖 AI-Powered Assistance (Grok Integration)
- **AI Tutor**: Chat with AI for explanations and guidance
- **Query Generator**: Convert natural language to KQL queries
- **Concept Explainer**: Get detailed explanations of operators and functions
- **Error Helper**: AI-powered error explanations and fixes
- **Exercise Solver**: Dynamic exercises with AI evaluation

### 💻 Query Lab
- Interactive query editor with syntax highlighting
- Real-time query execution
- Query history and favorites
- Result visualization (tables, charts)
- Export capabilities

### 📝 Quizzes & Assessments
- Interactive quizzes for each module
- AI-generated practice questions
- Immediate feedback and explanations
- Score tracking and analytics

### 📊 Progress Tracking
- Comprehensive dashboard with stats
- Points and gamification system
- Badge system for achievements
- Learning streak tracking
- Progress reports

### 🎨 Modern UI/UX
- Dark/Light theme support
- Responsive design
- Intuitive navigation
- Accessible interface
- Mobile-friendly

## 🚀 Getting Started

### Prerequisites

- Python 3.8 or higher
- Grok xAI API key (get from [x.ai](https://x.ai))
- (Optional) Azure Kusto cluster credentials for live data

### Installation

1. **Clone or download this repository**

```bash
cd kql_learning_app
```

2. **Install dependencies**

```bash
pip install -r requirements.txt
```

3. **Configure environment variables**

Copy `.env.example` to `.env` and add your API keys:

```bash
cp .env.example .env
```

Edit `.env`:
```
XAI_API_KEY=your_actual_grok_api_key_here
USE_DEMO_DATA=True
```

4. **Run the application**

```bash
streamlit run app.py
```

The app will open in your browser at `http://localhost:8501`

## 📖 Usage Guide

### For Beginners

1. **Start with the Home page** to see your dashboard
2. **Visit Learn KQL** and begin with "Introduction to KQL"
3. **Complete modules sequentially** for the best learning experience
4. **Use the Query Lab** to practice what you've learned
5. **Ask the AI Tutor** whenever you're stuck
6. **Take quizzes** to test your knowledge

### For Intermediate/Advanced Users

1. **Jump to specific modules** based on your interests
2. **Use the Query Generator** to speed up query writing
3. **Practice with custom exercises** in the AI Tutor
4. **Explore advanced optimization techniques**
5. **Connect your own Azure cluster** for real-world practice

## 🎯 Learning Path

### Beginner Level (3 modules)
- Introduction to KQL
- Basic Operators (where, project, take)
- Search & Filter Techniques

### Intermediate Level (3 modules)
- Aggregation Functions
- Join Operations
- Time Series Analysis

### Advanced Level (3 modules)
- User-Defined Functions
- Advanced Analytics
- Query Optimization

## 🏗️ Project Structure

```
kql_learning_app/
├── app.py                          # Main application entry point
├── requirements.txt                # Python dependencies
├── .env.example                    # Environment template
├── README.md                       # This file
├── modules/                        # Feature modules
│   ├── home.py                    # Home/dashboard page
│   ├── query_interface.py         # Query lab
│   ├── ai_tutor.py               # AI assistant features
│   ├── learning_modules.py        # Learning content
│   ├── quizzes.py                # Quiz system
│   └── progress_tracker.py        # Progress dashboard
├── utils/                         # Utility functions
│   ├── session_state.py          # State management
│   ├── theme_manager.py          # UI theming
│   ├── ai_helper.py              # Grok API integration
│   └── kusto_connector.py        # KQL execution
└── assets/                        # Images and resources
```

## 🔧 Configuration

### API Configuration

#### Grok xAI API
Required for AI features. Get your key from [x.ai](https://x.ai).

```env
XAI_API_KEY=xai-your-key-here
```

#### Azure Kusto (Optional)
For connecting to real Azure Data Explorer clusters:

```env
KUSTO_CLUSTER=https://your-cluster.kusto.windows.net
KUSTO_DATABASE=YourDatabase
USE_DEMO_DATA=False
```

### App Settings

Customize in `.env`:

```env
APP_TITLE=Must Learn KQL Learning Hub
APP_DEBUG=False
USE_DEMO_DATA=True
```

## 🎮 Gamification

### Points System
- Complete module: 50-150 points
- Run query: 10 points
- Complete quiz: 10 points per correct answer
- Solve exercise: 25-50 points

### Badges
- **KQL Novice**: Earn 100 points
- **KQL Practitioner**: Earn 500 points
- **KQL Expert**: Earn 1000 points
- **Week Warrior**: 7-day learning streak
- **Month Master**: 30-day learning streak
- **Perfect Score**: 100% on any quiz

## 🛠️ Development

### Running in Development Mode

```bash
# With auto-reload
streamlit run app.py --server.runOnSave true

# With debugging
streamlit run app.py --logger.level debug
```

### Adding New Modules

1. Edit `modules/learning_modules.py`
2. Add module definition to `get_all_modules()`
3. Include content, examples, and exercises

### Customizing Themes

Edit `utils/theme_manager.py` to customize colors and styles.

## 📝 Sample Queries

Try these in the Query Lab:

```kql
// Basic filtering
StormEvents
| where State == "TEXAS"
| take 10

// Aggregation
StormEvents
| summarize EventCount=count() by State
| top 10 by EventCount desc

// Time series
StormEvents
| where StartTime > ago(30d)
| summarize count() by bin(StartTime, 1d)
| render timechart
```

## 🤝 Contributing

Contributions are welcome! Areas for improvement:

- Additional learning modules
- More quiz questions
- Enhanced AI features
- Performance optimizations
- UI/UX improvements

## 📚 Resources

- [Must Learn KQL Series](https://github.com/rod-trent/MustLearnKQL)
- [KQL Documentation](https://learn.microsoft.com/en-us/azure/data-explorer/kusto/query/)
- [Azure Data Explorer](https://azure.microsoft.com/en-us/services/data-explorer/)
- [Grok AI](https://x.ai)

## 🐛 Troubleshooting

### API Key Issues
- Verify your Grok API key is correct in `.env`
- Check that `.env` file is in the app root directory
- Ensure no extra spaces around the key

### Connection Issues
- Demo data works without Azure setup
- For Azure connections, verify credentials
- Check network/firewall settings

### Module Not Found Errors
- Install all requirements: `pip install -r requirements.txt`
- Check Python version (3.8+)
- Use a virtual environment

## 📄 License

This project is created for educational purposes based on the "Must Learn KQL" series.

## 👤 Author

**Rod**
- Substack: https://rodtrent.substack.com/ 
- GitHub: https://github.com/rod-trent/ 

## 🙏 Acknowledgments

- "Must Learn KQL" series by Rod Trent
- Grok xAI for AI capabilities
- Streamlit for the framework

## 📧 Support

For questions or issues:
1. Check the AI Tutor in the app
2. Review the troubleshooting section
3. Submit feedback through the app

---

**Happy Learning! 🚀**

Master KQL with interactive lessons, AI-powered assistance, and hands-on practice.


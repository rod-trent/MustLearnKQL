# Contributing to Must Learn KQL Learning Hub

First off, thank you for considering contributing to the Must Learn KQL Learning Hub! It's people like you that make this project a great learning resource for the community.

## Table of Contents

- [Code of Conduct](#code-of-conduct)
- [What We're Looking For](#what-were-looking-for)
- [How Can I Contribute?](#how-can-i-contribute)
  - [Reporting Bugs](#reporting-bugs)
  - [Suggesting Enhancements](#suggesting-enhancements)
  - [Adding Learning Content](#adding-learning-content)
  - [Code Contributions](#code-contributions)
- [Development Setup](#development-setup)
- [Coding Guidelines](#coding-guidelines)
- [Testing Guidelines](#testing-guidelines)
- [Pull Request Process](#pull-request-process)
- [Community](#community)

---

## Code of Conduct

This project and everyone participating in it is governed by our commitment to creating a welcoming and inclusive environment. By participating, you are expected to:

- **Be respectful** - Treat all contributors with respect and consideration
- **Be collaborative** - Work together to improve the project
- **Be patient** - Remember that everyone was a beginner once
- **Be constructive** - Provide helpful feedback and suggestions
- **Be inclusive** - Welcome contributors of all backgrounds and experience levels

We do not tolerate harassment, discrimination, or inappropriate behavior of any kind.

---

## What We're Looking For

We welcome contributions in many forms:

### 🐛 Bug Reports
Help us identify and fix issues in the application.

### ✨ Feature Suggestions
Ideas for new features or improvements to existing ones.

### 📚 Learning Content
- New modules and lessons
- Quiz questions
- Practice exercises
- Code examples
- Explanatory content

### 💻 Code Improvements
- Bug fixes
- Performance optimizations
- New features
- UI/UX enhancements
- Test coverage

### 📖 Documentation
- Tutorials and guides
- Code documentation
- README improvements
- API documentation

### 🌐 Translations
Help make the app accessible to non-English speakers (future feature).

### 🎨 Design
- UI mockups
- Icons and graphics
- Theme improvements
- Accessibility enhancements

---

## How Can I Contribute?

### Reporting Bugs

**Before Submitting a Bug Report:**

1. **Check the FAQ** - Your question might already be answered
2. **Search existing issues** - The bug might already be reported
3. **Test with the latest version** - The bug might already be fixed
4. **Verify it's reproducible** - Make sure you can reproduce the issue

**How to Submit a Good Bug Report:**

Create an issue on GitHub with the following information:

```markdown
**Bug Description**
A clear and concise description of what the bug is.

**To Reproduce**
Steps to reproduce the behavior:
1. Go to '...'
2. Click on '...'
3. Scroll down to '...'
4. See error

**Expected Behavior**
A clear description of what you expected to happen.

**Screenshots**
If applicable, add screenshots to help explain the problem.

**Environment:**
- OS: [e.g., Windows 10, macOS 13, Ubuntu 22.04]
- Python Version: [e.g., 3.10.5]
- Browser: [e.g., Chrome 120, Firefox 121]
- App Version: [e.g., 1.0.0]

**Additional Context**
Add any other context about the problem here.

**Error Logs**
```


**Labels to Use:**
- `bug` - Something isn't working
- `critical` - Severe bug that breaks core functionality
- `ui` - Visual or interface issues
- `performance` - Performance-related issues

---

### Suggesting Enhancements

**Before Submitting an Enhancement:**

1. **Check the roadmap** - It might already be planned
2. **Search existing issues** - It might already be suggested
3. **Consider the scope** - Will this benefit most users?

**How to Submit a Good Enhancement Suggestion:**

```markdown
**Feature Description**
A clear and concise description of the feature.

**Problem It Solves**
Explain the problem this feature would solve or the value it would add.

**Proposed Solution**
Describe how you envision this feature working.

**Alternatives Considered**
Describe any alternative solutions you've considered.

**Additional Context**
Add any mockups, examples, or other context.

**Would you be willing to implement this?**
[ ] Yes, I can implement this
[ ] I can help but need guidance
[ ] I can't implement but want to suggest it
```

**Labels to Use:**
- `enhancement` - New feature or request
- `ui-ux` - User interface improvements
- `content` - Learning content additions
- `ai` - AI/ML related features
- `integration` - External integrations

---

### Adding Learning Content

Learning content contributions are especially valuable! Here's how:

#### Adding a New Module

1. **Plan Your Module:**
   - Decide on the topic and learning objectives
   - Determine the difficulty level (Beginner/Intermediate/Advanced)
   - Estimate completion time
   - Plan the structure (sections, examples, exercises)

2. **Create the Module:**

Edit `modules/learning_modules.py` and add your module to the `get_all_modules()` function:

```python
{
    'id': 'your_module_id',  # Use lowercase with underscores
    'name': 'Your Module Name',
    'level': 'Beginner',  # or 'Intermediate', 'Advanced'
    'icon': '🎯',  # Choose an appropriate emoji
    'duration': '20 min',  # Estimated completion time
    'points': 75,  # Points awarded: Beginner=50-75, Intermediate=75-100, Advanced=100-150
    'description': 'Brief description of what learners will learn in this module.',
    
    # Main content sections
    'content': [
        {
            'title': 'Section 1 Title',
            'text': '''
Your explanation here. Use markdown formatting:
- **Bold** for emphasis
- `code` for KQL keywords
- Clear, concise language

Break into digestible paragraphs.
            ''',
            'examples': [
                {
                    'code': 'StormEvents\n| take 10',
                    'explanation': 'Clear explanation of what this code does'
                }
            ],
            'demo': 'StormEvents\n| take 5  // Optional interactive demo query'
        },
        # Add more sections as needed
    ],
    
    # Key takeaways (3-5 bullet points)
    'takeaways': [
        'First key learning point',
        'Second key learning point',
        'Third key learning point'
    ],
    
    # Practice exercises
    'practice': [
        {
            'title': 'Practice Exercise Title',
            'description': 'What the learner should accomplish',
            'hints': [
                'Hint 1: Start with...',
                'Hint 2: Remember to...'
            ],
            'solution': 'StormEvents\n| where State == "TEXAS"\n| take 10'
        }
    ],
    
    # Challenge exercises
    'exercises': [
        {
            'title': 'Challenge Exercise',
            'difficulty': 'Medium',
            'description': 'More complex task for learners to solve',
            'dataset': 'StormEvents'
        }
    ],
    
    'quiz_questions': 10  # Number of questions for the module quiz
}
```

3. **Content Guidelines:**

**Writing Style:**
- Use clear, simple language
- Explain concepts before showing code
- Include "why" not just "how"
- Use real-world analogies
- Be encouraging and supportive

**Code Examples:**
- Start with simple examples
- Progress to more complex ones
- Include comments in code
- Explain each operator used
- Show both correct and incorrect examples (with explanations)

**Structure:**
- Each section should be 3-7 minutes of content
- Include at least 2 code examples per section
- Provide both simple and complex examples
- End with a summary of key points

4. **Submit Your Module:**
   - Create a pull request
   - Include a brief description
   - Tag it with `content` label
   - Request review from maintainers

#### Adding Quiz Questions

Edit the quiz file for the relevant module or use the AI generation feature:

```python
{
    'question': 'Clear, unambiguous question text?',
    'options': [
        'A. First option',
        'B. Second option',
        'C. Third option',
        'D. Fourth option'
    ],
    'correct': 'A',  # The letter of the correct answer
    'explanation': 'Detailed explanation of why A is correct and why others are not.'
}
```

**Question Guidelines:**
- One clear correct answer
- Three plausible distractors
- Avoid "all of the above" or "none of the above"
- Test understanding, not memorization
- Include explanations for all options

---

### Code Contributions

#### Development Setup

1. **Fork the Repository**

Click the "Fork" button on GitHub, then clone your fork:

```bash
git clone https://github.com/YOUR_USERNAME/MustLearnKQL.git
cd MustLearnKQL/App
```

2. **Set Up Development Environment**

```bash
# Create virtual environment
python -m venv venv

# Activate virtual environment
# Windows:
venv\Scripts\activate
# Mac/Linux:
source venv/bin/activate

# Install dependencies
pip install -r requirements.txt

# Install development dependencies
pip install -r requirements-dev.txt  # If available
```

3. **Configure Environment**

```bash
# Copy environment template
cp .env.example .env

# Add your API keys
# Edit .env with your favorite editor
```

4. **Create a Branch**

```bash
git checkout -b feature/your-feature-name
# or
git checkout -b fix/bug-description
```

**Branch Naming Convention:**
- `feature/` - New features
- `fix/` - Bug fixes
- `docs/` - Documentation changes
- `refactor/` - Code refactoring
- `test/` - Adding tests
- `style/` - Code style/formatting

5. **Make Your Changes**

Follow the coding guidelines below and test thoroughly.

6. **Commit Your Changes**

```bash
git add .
git commit -m "Brief description of changes"
```

**Commit Message Guidelines:**
- Use present tense ("Add feature" not "Added feature")
- Use imperative mood ("Move cursor to..." not "Moves cursor to...")
- First line: Brief summary (50 chars or less)
- Blank line
- Detailed description if needed

Examples:
```
Add query syntax highlighting to editor

Implements syntax highlighting for KQL queries using
streamlit-ace component. Adds color coding for:
- Keywords (where, project, summarize)
- Operators (==, !=, >)
- Functions (count, sum, avg)
```

7. **Push to GitHub**

```bash
git push origin feature/your-feature-name
```

8. **Create Pull Request**

Go to GitHub and click "New Pull Request"

---

## Coding Guidelines

### Python Style

Follow PEP 8 with these specific guidelines:

**General:**
```python
# Use 4 spaces for indentation (not tabs)
# Maximum line length: 100 characters
# Two blank lines between top-level definitions
# One blank line between method definitions

# Good
def calculate_score(correct, total):
    """Calculate percentage score."""
    return (correct / total) * 100

# Bad
def calculate_score(correct,total):
    return (correct/total)*100
```

**Naming Conventions:**
```python
# Functions and variables: lowercase_with_underscores
def get_user_progress():
    user_points = 100
    
# Classes: CapitalizedWords
class QueryExecutor:
    pass

# Constants: UPPERCASE_WITH_UNDERSCORES
MAX_QUERY_LENGTH = 10000
DEFAULT_POINTS = 50

# Private methods: _leading_underscore
def _internal_helper():
    pass
```

**Imports:**
```python
# Standard library imports first
import os
import sys
from datetime import datetime

# Third-party imports second
import streamlit as st
import pandas as pd

# Local imports last
from utils.session_state import initialize_session_state
from modules.home import render_home
```

**Docstrings:**
```python
def execute_query(query, use_demo=True):
    """
    Execute a KQL query and return results.
    
    Args:
        query (str): The KQL query to execute
        use_demo (bool): Whether to use demo data (default: True)
    
    Returns:
        pd.DataFrame: Query results as a pandas DataFrame
    
    Raises:
        ValueError: If query is empty or invalid
        ConnectionError: If cluster connection fails
    
    Example:
        >>> results = execute_query("StormEvents | take 10")
        >>> print(len(results))
        10
    """
    pass
```

### Streamlit Specific

**Session State:**
```python
# Always initialize in session_state.py
def initialize_session_state():
    if 'key_name' not in st.session_state:
        st.session_state.key_name = default_value

# Use descriptive key names
st.session_state.user_query_history  # Good
st.session_state.qh  # Bad
```

**Component Organization:**
```python
# Good - organized and clear
def render_dashboard():
    """Render the main dashboard."""
    st.title("Dashboard")
    
    col1, col2, col3 = st.columns(3)
    
    with col1:
        render_progress_metric()
    
    with col2:
        render_points_metric()
    
    with col3:
        render_streak_metric()

# Bad - monolithic
def render_dashboard():
    st.title("Dashboard")
    st.metric("Progress", "50%")
    st.metric("Points", "500")
    st.metric("Streak", "7")
```

**Error Handling:**
```python
# Always handle errors gracefully
try:
    result = execute_query(query)
    st.success("Query executed successfully!")
    display_results(result)
except ValueError as e:
    st.error(f"Invalid query: {str(e)}")
except ConnectionError as e:
    st.error(f"Connection failed: {str(e)}")
    st.info("Try using demo mode instead.")
except Exception as e:
    st.error(f"Unexpected error: {str(e)}")
    st.warning("Please report this issue on GitHub.")
```

**Loading States:**
```python
# Show loading indicators for slow operations
with st.spinner("Executing query..."):
    result = execute_query(query)

# For very quick operations, skip the spinner
result = simple_calculation()
```

### AI Integration

**API Calls:**
```python
# Always handle API failures
def chat_with_grok(message):
    try:
        client = get_grok_client()
        response = client.chat.completions.create(
            model="grok-3",
            messages=[{"role": "user", "content": message}]
        )
        return response.choices[0].message.content
    except Exception as e:
        # Provide helpful fallback
        return get_fallback_response('chat')
```

**Rate Limiting:**
```python
# Add delays between API calls if making multiple requests
import time

for item in items:
    response = call_api(item)
    time.sleep(0.5)  # Avoid rate limits
```

**Caching:**
```python
# Cache expensive operations
@st.cache_data(ttl=3600)  # Cache for 1 hour
def get_concept_explanation(topic):
    return explain_concept(topic)
```

---

## Testing Guidelines

### Manual Testing Checklist

Before submitting a pull request, test:

**Functionality:**
- [ ] All new features work as intended
- [ ] Existing features still work
- [ ] Error handling works correctly
- [ ] Edge cases are handled

**UI/UX:**
- [ ] Layout looks good on desktop
- [ ] Layout works on mobile
- [ ] Dark theme works
- [ ] Light theme works
- [ ] Loading states display correctly
- [ ] Error messages are clear

**Performance:**
- [ ] Page loads quickly
- [ ] No unnecessary API calls
- [ ] Large datasets display efficiently
- [ ] No memory leaks

**Compatibility:**
- [ ] Works on Windows
- [ ] Works on macOS
- [ ] Works on Linux
- [ ] Works in Chrome
- [ ] Works in Firefox
- [ ] Works in Safari

### Automated Tests

We're working on adding automated tests. If you'd like to contribute test coverage, that would be greatly appreciated!

**Test Structure:**
```python
# tests/test_query_execution.py
import pytest
from utils.kusto_connector import execute_kql_query

def test_basic_query():
    """Test basic query execution."""
    query = "StormEvents | take 10"
    result = execute_kql_query(query)
    assert len(result) == 10

def test_invalid_query():
    """Test invalid query handling."""
    query = "InvalidTable | take 10"
    with pytest.raises(ValueError):
        execute_kql_query(query)
```

---

## Pull Request Process

### Before Submitting

1. **Update Documentation:**
   - Update README.md if needed
   - Add/update docstrings
   - Update CHANGELOG.md

2. **Test Thoroughly:**
   - Run through manual testing checklist
   - Test on different operating systems if possible
   - Verify no existing functionality broke

3. **Clean Up:**
   - Remove debug print statements
   - Remove commented-out code
   - Ensure consistent formatting
   - Remove unused imports

### Creating the Pull Request

1. **Push Your Branch:**
```bash
git push origin feature/your-feature-name
```

2. **Open PR on GitHub:**
   - Click "New Pull Request"
   - Select your branch
   - Fill out the PR template

3. **PR Template:**
```markdown
## Description
Brief description of what this PR does.

## Type of Change
- [ ] Bug fix (non-breaking change that fixes an issue)
- [ ] New feature (non-breaking change that adds functionality)
- [ ] Breaking change (fix or feature that would cause existing functionality to not work as expected)
- [ ] Documentation update
- [ ] Code refactoring
- [ ] Performance improvement

## Motivation and Context
Why is this change required? What problem does it solve?

## How Has This Been Tested?
Describe the tests you ran and their results.

## Screenshots (if applicable)
Add screenshots for UI changes.

## Checklist
- [ ] My code follows the project's style guidelines
- [ ] I have performed a self-review of my code
- [ ] I have commented my code, particularly in hard-to-understand areas
- [ ] I have made corresponding changes to the documentation
- [ ] My changes generate no new warnings
- [ ] I have tested my changes thoroughly
- [ ] Any dependent changes have been merged and published

## Related Issues
Fixes #(issue number)
```

### Review Process

1. **Automated Checks:**
   - Code style checks (if configured)
   - Basic tests (if configured)
   - Merge conflict checks

2. **Maintainer Review:**
   - Code quality review
   - Functionality verification
   - Documentation check
   - Testing verification

3. **Feedback:**
   - Respond to review comments
   - Make requested changes
   - Push updates to your branch
   - Request re-review

4. **Merge:**
   - Once approved, maintainers will merge
   - Your PR will be closed
   - Changes will appear in the next release

### After Merge

- **Celebrate!** 🎉 You've contributed to the project!
- Your contribution will be credited in the CHANGELOG
- You'll be added to the contributors list
- Consider contributing more!

---

## Community

### Communication Channels

**GitHub Discussions:**
- Questions and answers
- Feature discussions
- General community chat

**GitHub Issues:**
- Bug reports
- Feature requests
- Technical discussions

**Social Media:**
- Follow updates on Twitter/X
- Join LinkedIn discussions
- Subscribe to the newsletter

### Recognition

Contributors are recognized in several ways:

1. **Contributors List:**
   - Added to README.md
   - Credited in release notes

2. **Special Recognition:**
   - Top contributors highlighted
   - Featured in blog posts
   - Special badges (coming soon)

3. **Author Credit:**
   - Content contributors credited in modules
   - Code contributors in commit history

---

## Questions?

Still have questions? We're here to help!

**Before Asking:**
1. Check existing documentation
2. Search GitHub issues and discussions
3. Review the FAQ in the README

**How to Ask:**
- Open a GitHub Discussion for general questions
- Open an issue for bug reports or feature requests
- Be specific and provide context
- Include relevant code/screenshots

**We promise to:**
- Be helpful and respectful
- Guide you through the contribution process
- Value your time and effort

---

## Thank You!

Thank you for contributing to the Must Learn KQL Learning Hub! Every contribution, no matter how small, helps make this project better for everyone.

Your efforts help thousands of people learn KQL more effectively, and that's something to be proud of.

Happy Contributing! 🚀



---

*Last Updated: January 2026*  
*Maintained by: Rod Trent and the community*

# 🗓 Twitter / X — Schedule to Official Queue

A Tampermonkey userscript that automates Twitter/X's native tweet scheduler, allowing you to batch schedule multiple tweets with text, images, and precise date/time settings.

## ✨ Features

- **Batch Tweet Scheduling** - Queue multiple tweets and schedule them all at once
- **Full Text Support** - Character-by-character typing recognized by Twitter's React engine
- **Image Attachments** - Attach optional images to scheduled tweets
- **Native Scheduler** - Uses Twitter's official scheduler (no API hacking)
- **Full-Screen UI** - Beautiful split-screen interface (input form + queue list)
- **Edit Pending Tweets** - Click any pending tweet to edit it before scheduling
- **Delete from Queue** - Remove tweets from the queue before scheduling
- **Status Tracking** - Visual indicators for pending, processing, completed, and failed tweets
- **Smart Notifications** - Toast notifications that stack from top-right, newest on top
- **Multi-Tweet Delays** - 3-second delays between scheduling tweets to avoid rate limiting

## 🚀 Installation

### Prerequisites
- **Tampermonkey** browser extension (install from [Chrome Web Store](https://chrome.google.com/webstore/detail/tampermonkey/dhdgffkkebhmkfjojejmpbldmpobp55f), [Firefox Add-ons](https://addons.mozilla.org/en-US/firefox/addon/tampermonkey/), or similar)
- Twitter/X account
- Chrome, Firefox, Edge, or Safari

### Steps

1. **Open Tampermonkey Dashboard**
   - Click the Tampermonkey extension icon
   - Select "Dashboard"

2. **Create New Script**
   - Click "Create a new script"
   - Delete the default template

3. **Copy & Paste Script**
   - Copy the entire script from [Twitter Batch Scheduler Script](https://github.com/bleakbanksy/twitter-batch-scheduler/blob/main/twitter-batch-scheduler-script)
   - Paste into the Tampermonkey editor
   - Press `Ctrl+S` / `Cmd+S` to save

4. **Navigate to Twitter/X**
   - Go to [twitter.com](https://twitter.com) or [x.com](https://x.com)
   - The script runs automatically on page load
   - Look for the **"Batch Tweet Scheduler"** button in the top-right corner

## 📖 How to Use

### Basic Workflow

1. **Click the Button**
   - Click **"Batch Tweet Scheduler"** button (top-right corner)

2. **Fill in Tweet Details**
   - **TWEET TEXT** - Type your tweet content (max 280 characters)
   - **SCHEDULED DATE & TIME** - Pick when to post (must be future date/time)
   - **IMAGE (OPTIONAL)** - Attach an image (click to select file)

3. **Add to Queue**
   - Click **"➕ Add to Queue"**
   - Tweet appears in the right panel with status **⏳ PENDING**

4. **Repeat for More Tweets**
   - Add as many tweets as you want before scheduling
   - Edit pending tweets by clicking them
   - Delete by clicking the ✕ button

5. **Schedule All**
   - Click **"🚀 Schedule All"** when ready
   - Each tweet is automatically scheduled with 3-second delays
   - Watch the status change: ⏳ → 🔄 → ✅

### Editing Pending Tweets

- Click any **PENDING** tweet in the queue
- Its details load into the left form
- Edit the text, date/time, or image
- The tweet is removed from queue
- Click "Add to Queue" again to save changes

## ⚙️ Features Explained

### Smart Text Entry
- Types text character-by-character with realistic keyboard events
- Automatically triggers Twitter's React state handlers
- Text appears exactly as user input (not as placeholder)

### Image Handling
- Converts images to base64 format
- Supports JPEG, PNG, GIF, WebP
- Shows preview before scheduling

### Date/Time Selection
- Uses HTML5 datetime-local input
- Validates dates are in the future
- Converts to Twitter's schedule picker format
- Handles timezone automatically

### Queue Management
- **Pending (⏳)** - Ready to schedule
- **Processing (🔄)** - Currently being scheduled
- **Completed (✅)** - Successfully added to Twitter queue
- **Failed (❌)** - Error during scheduling (check browser console)

### Notifications
- **Blue notifications** - Success messages
- **Red notifications** - Error messages
- Stack vertically with automatic positioning
- Auto-dismiss after 5 seconds

## 🛡️ Safety & Compliance

### Is It Safe?
✅ **Yes, this script is safe:**
- No external API calls
- No credential or data theft
- Uses Twitter's **official scheduler** (not API hacking)
- All code is open-source and readable
- Runs entirely in your browser

### Twitter ToS Compliance
- Uses native Twitter features only
- 3-second delays between scheduling (built-in rate limiting)
- No mass automation or spam capabilities
- Designed for legitimate content creators

### Usage Recommendations

**Safe Limits:**
- 5-10 tweets per session: **Very safe** ✅
- 10-20 tweets per session: **Safe** ✅
- 20-50 tweets per session: **Moderate risk** ⚠️
- 50+ tweets per session: **High risk** ⚠️

**Best Practices:**
1. Schedule 5-10 tweets, then stop
2. Wait 1 hour before scheduling more
3. Spread tweets across different days
4. Vary content (don't schedule identical tweets)
5. Use different post times

**If Flagged:**
- Level 1: Scheduling disabled for 12-48 hours (auto-resets)
- Level 2: Temp restriction 3-7 days
- Level 3: Tweet deleted or reach reduced (appealable)
- Level 4: Account suspension (very rare, very reversible)

Most restrictions are **temporary and auto-reset** after 24-48 hours.

## 🐛 Troubleshooting

### Button Doesn't Appear
- **Solution**: Wait 2-3 seconds after page loads
- Check Tampermonkey is enabled
- Verify you're on twitter.com or x.com

### Text Not Being Entered
- **Solution**: Make sure you use the official compose box
- Click "Post" button in Twitter to open it
- Wait for the form to fully load

### Image Won't Attach
- **Solution**: Check image file size (keep under 5MB)
- Try PNG or JPEG formats
- Refresh page and try again

### Date Picker Error: "Can't schedule in past"
- **Solution**: Make sure date is in the future
- Check your timezone is correct
- Set date at least 5 minutes from now

### Schedule Button Disabled
- **Solution**: Make sure you filled in all required fields:
  - Tweet text (at least 1 character)
  - Future date/time

### Tweets Not Appearing in Queue
- **Solution**: Check error messages in red notifications
- Open browser console (F12) for detailed logs
- Search console for "[TwitterScheduler]" messages

## 📝 Advanced Configuration

### Modify Delays
Edit this line to change delay between tweets:
```javascript
await sleep(3000); // 3000ms = 3 seconds
```

### Change Button Position
Find `buildFAB()` function and modify:
```javascript
position: 'fixed', top: '24px', right: '24px', // Change these values
```

### Customize Colors
Find `showToast()` function to change notification colors:
```javascript
background: isError ? '#c0392b' : '#1d9bf0', // Modify hex colors
```

## 📊 Performance

- **Memory usage**: ~5-10MB typical
- **CPU usage**: Minimal, only active during scheduling
- **Network**: Only communicates with twitter.com
- **Battery**: Negligible impact

## 🔧 Technical Details

### Browser Support
- ✅ Chrome/Chromium (v90+)
- ✅ Firefox (v88+)
- ✅ Edge (v90+)
- ✅ Safari (with Tampermonkey/Userscripts)

### Technologies Used
- **Vanilla JavaScript** - No external dependencies
- **Tampermonkey** - Userscript runner
- **Twitter's Native Scheduler** - Official feature only
- **MutationObserver** - DOM change detection
- **React Event Handling** - Bypass Twitter's React framework

### How It Works
1. Detects Twitter's native compose box
2. Simulates realistic keyboard input (character-by-character)
3. Triggers Twitter's React state handlers
4. Attaches images as base64 encoded data
5. Opens Twitter's native schedule picker
6. Fills dropdown values using native HTMLSelectElement setters
7. Waits for DOM stability between changes (prevents race conditions)
8. Clicks confirmation and schedule buttons
9. Adds tweet to official Twitter scheduled queue

## 📄 License

MIT License - Use freely, modify for personal use

## ⚖️ Disclaimer

This script is provided as-is for educational and personal use. The author is not responsible for:
- Account restrictions or suspension
- Violation of Twitter's Terms of Service
- Unintended scheduling or content issues
- Data loss or corruption

Use responsibly. Always comply with Twitter's platform policies.

## 🤝 Contributing

Have improvements? Found a bug?
1. Test thoroughly before reporting
2. Document the issue clearly
3. Include browser and Twitter version info
4. Provide steps to reproduce


## 🎯 Roadmap

Potential future features:
- [ ] Local storage persistence (queue survives page refresh)
- [ ] Bulk import from CSV
- [ ] Custom keyboard shortcuts
- [ ] Thread scheduling support
- [ ] Reply scheduling
- [ ] Dark mode toggle (already uses dark theme)
- [ ] Multi-account support

## ⭐ Tips for Best Results

1. **Always preview** - Double-check text and dates before scheduling
2. **Space them out** - Don't schedule 100 tweets at once
3. **Mix content** - Vary topics and types
4. **Monitor Twitter** - Check scheduled queue manually to verify
5. **Check console logs** - Useful for debugging issues

---

**Made with ❤️ for content creators and social media managers**

*Last updated: February 22, 2026*
*Version: 3.0.0*

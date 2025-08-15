# GitHub Discussions to ProductLane
Automatically sync GitHub Discussions to ProductLane insights for better product feedback management.

# What it does
 - 🔄 Auto-sync: New discussions and comments in specific categories are automatically sent to ProductLane
 - 👍 Upvote tracking: Captures current discussion upvotes for prioritization
 - 📝 Smart content: Sends original post content for new discussions, only new comment content for updates
 - 🏷️ Clear labeling: Prefixes titles with [NEW], [COMMENT], [EDITED] etc.

# Setup

## 1. Enable GitHub Discussions

 - Go to your repo Settings → Features → Check "Discussions"
 - Create a category called "Feature Requests" (or customize the category name in the workflow)

## 2. Get ProductLane API Token

 - Get your API token from ProductLane
 - Add it as a repository secret: PRODUCTLANE_API_TOKEN

## 3. Add the Workflow

 - Copy .github/workflows/productlane-sync.yml to your repo
 - Customize the discussion category filter if needed

## 4. Test

 - Create a discussion in the "Feature Requests" category
 - Check the Actions tab to see if it runs successfully
 - Verify the insight appears in ProductLane

# Configuration
 - Edit the if condition in the workflow: `yamlif: github.event.discussion.category.name == 'Feature Requests'`
 - Multiple Categories: `yamlif: github.event.discussion.category.name == 'Feature Requests' || github.event.discussion.category.name == 'Bug Reports'`

# What gets synced

 - ✅ New discussions → Full discussion content
 - ✅ New comments → Comment content only
 - ✅ Discussion/comment edits → Updated content
 - ✅ Current upvote count → Always fetched fresh
 - ✅ Author info → GitHub username and generated email

# ProductLane Integration

Each insight includes:

```
Title: [PREFIX] Discussion Title (👍 upvotes)
Content: Discussion/comment text + upvote footer
Pain Level: Set to "UNKNOWN"
Contact: GitHub username + @github.local email
Notifications: Slack enabled, email disabled
```

Perfect for turning community feedback into actionable product insights! 🚀

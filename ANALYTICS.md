# Vercel Web Analytics Setup

This project is configured with Vercel Web Analytics to track page views and user interactions.

## Installation

The `@vercel/analytics` package (v2.0.1) has been installed via npm:

```bash
npm install @vercel/analytics
```

## Configuration

For this static HTML site, Vercel Web Analytics is implemented using the script-based injection method, which is the recommended approach for sites without a build system or module bundler.

### Implementation in index.html

The following scripts are added in the `<head>` section (before the closing `</head>` tag):

```html
<script>window.va = window.va || function () { (window.vaq = window.vaq || []).push(arguments); };</script>
<script defer src="/_vercel/insights/script.js"></script>
```

This setup:
1. Initializes the analytics queue (`window.vaq`)
2. Loads the Vercel analytics script asynchronously
3. Automatically tracks page views and web vitals

## How It Works

When deployed on Vercel:
- The `/_vercel/insights/script.js` path is automatically served by Vercel's platform
- Analytics data is collected and sent to Vercel's analytics service
- Data appears in your Vercel project dashboard under the "Analytics" tab

## Viewing Analytics Data

1. Deploy this site to Vercel
2. Navigate to your project dashboard on vercel.com
3. Click on the "Analytics" tab
4. View page views, unique visitors, and top pages

## Local Development

During local development:
- The analytics script will attempt to load but won't track data
- No analytics data is sent from localhost
- This is the expected behavior and will not affect functionality

## Framework Notes

This project uses vanilla HTML/JavaScript without a build system. For projects using React, Next.js, Vue, or other frameworks with build steps, you would instead use:

```javascript
import { Analytics } from '@vercel/analytics/react'; // or /next, /vue, etc.
// Then add <Analytics /> component to your app
```

Since this is a static site, the script-based approach is the correct implementation.

## Documentation

For more information, see the official Vercel Web Analytics documentation:
- https://vercel.com/docs/analytics/quickstart
- https://vercel.com/docs/analytics

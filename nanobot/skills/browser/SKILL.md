---
name: browser
description: "Browser automation using Playwright. Navigate, interact with elements, take screenshots, and extract content from web pages."
metadata: {"nanobot":{"emoji":"🌐","requires":{"bins":[]}}}
---

# Browser Skill

Use this skill to automate web browser interactions using Playwright.

## Available Actions

### Navigation

```
// Navigate to a URL
browser action=navigate url="https://example.com"

// Alias for navigate
browser action=goto url="https://example.com"
```

### Click Elements

```
// Click an element using CSS selector
browser action=click selector="button.submit"
browser action=click selector="#login-btn"
```

### Fill Forms

```
// Fill an input field
browser action=fill selector="input[name='username']" value="myuser"

// Fill and press Enter
browser action=fill selector="input[name='search']" value="query" pressEnter=true
```

### Screenshots

```
// Take a screenshot
browser action=screenshot

// Screenshot specific element
browser action=screenshot selector=".result-card"

// Full page screenshot
browser action=screenshot fullPage=true

// Save to file
browser action=screenshot path="./screenshot.png"
```

### Get Content

```
// Get page content
browser action=content

// Get specific element content
browser action=content selector=".article-body"
```

### Execute JavaScript

```
// Run JavaScript in the browser
browser action=evaluate script="document.title"
browser action=evaluate script="window.location.href"
```

### Wait

```
// Wait for element to appear
browser action=wait selector=".loading-done"

// Wait for a duration (ms)
browser action=wait timeout=2000
```

### Page Information

```
// Get page title
browser action=getTitle

// Get current URL
browser action=getUrl

// Create new page/tab
browser action=newPage

// Close browser
browser action=close
```

### Keyboard & Mouse

```
// Press a key
browser action=press key="Enter"
browser action=press key="Escape"

// Hover over element
browser action=hover selector=".menu-item"

// Select dropdown option
browser action=select selector="select.country" value="US"
```

## Common Workflows

### Web Scraping

1. Navigate to the page
2. Wait for content to load
3. Extract the content

### Form Submission

1. Navigate to the form
2. Fill in the fields
3. Click submit button
4. Wait for response

### Login Flow

1. Navigate to login page
2. Fill username
3. Fill password
4. Click login button
5. Wait for redirect

## Notes

- Browser runs in headless mode by default
- All selectors use CSS selector syntax
- Screenshots return base64-encoded images
- Browser instance is shared across actions in a session
- Use `close` action to free resources when done

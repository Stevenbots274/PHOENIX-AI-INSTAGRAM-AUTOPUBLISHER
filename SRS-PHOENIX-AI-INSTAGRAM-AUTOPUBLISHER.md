# SRS — PHOENIX AI INSTAGRAM AUTOPUBLISHER

| Item | Value |
| --- | --- |
| **Platform Domain** | [https://instagram.senseiphoenix.name.ng](https://instagram.senseiphoenix.name.ng) |
| **Admin Subdomain** | [https://admin-instagram.senseiphoenix.name.ng](https://admin-instagram.senseiphoenix.name.ng) |
| **AI Provider Base URL** | [https://combined-alidia-suhailtechlnfo-01b0509f.koyeb.app](https://combined-alidia-suhailtechlnfo-01b0509f.koyeb.app) |
| **Platform Type** | AI-powered Instagram content generation, scheduling, and automatic publishing system |
| **Primary AI Capability** | Text generation |
| **Primary Publishing Integration** | Official Meta/Instagram API |
| **Web Search** | Tavily (primary), DuckDuckGo and Serper (backups) |
| **Notifications** | Internal only (no email / SMTP) |
| **Supported Deployment** | Koyeb, Render, Railway |

---

# Chapter 1 — Platform, User Authentication and Instagram Connection

## 1.1 Platform Overview

The system shall be a dedicated web application hosted at:

[https://instagram.senseiphoenix.name.ng](https://instagram.senseiphoenix.name.ng)

The platform shall allow users to:

1. Create an account.
2. Log in.
3. Connect their Instagram Professional account.
4. Configure an AI content strategy.
5. Generate Instagram content using the configured text AI.
6. Create or select supporting media.
7. Schedule content.
8. Automatically publish content to Instagram.
9. Monitor publishing activity.
10. Manage previously generated content.

The platform shall be designed so that a normal user does not need to understand Meta APIs, OAuth, access tokens, API keys, backend endpoints, or technical authentication processes.

The intended user experience is:

```
Visit Website
    ↓
Create Account / Login
    ↓
Dashboard
    ↓
Connect Instagram
    ↓
Instagram Authorization
    ↓
Automatic Backend Processing
    ↓
Instagram Connected
    ↓
Configure Autoposter
    ↓
Start Autopilot
```

## 1.2 Landing Page

When a visitor opens [https://instagram.senseiphoenix.name.ng](https://instagram.senseiphoenix.name.ng), they shall see a professional landing page explaining the service.

The landing page shall clearly communicate that the platform allows users to automate Instagram content using AI.

The landing page shall contain:

- Brand / logo
- Product name
- Short product description
- How it works
- Main features
- AI content generation explanation
- Instagram automation explanation
- Security information
- Login button
- Create Account / Get Started button

**Primary CTA:** Get Started

**Secondary CTA:** Login

## 1.3 User Registration

New users shall be able to create an account.

The registration system shall support:

- Email address
- Password
- Password confirmation
- Secure session creation

The system shall validate:

- Email format
- Password requirements
- Duplicate email
- Required fields

Email verification shall **not** be required. After successful registration, the user shall be authenticated immediately and redirected to the dashboard.

## 1.4 User Login

Existing users shall be able to log in.

The login flow shall:

1. Receive credentials.
2. Validate credentials.
3. Authenticate the user.
4. Create a secure session.
5. Redirect the user to the dashboard.

The system shall not require the user to repeatedly authenticate with the application during normal use.

## 1.5 User Dashboard

The dashboard shall be the main control center.

The dashboard shall contain:

- Instagram connection status
- Autoposter status
- Next scheduled post
- Recent posts
- Content queue
- AI generation status
- Publishing statistics
- Quick actions
- Settings

**Primary actions:**

- Connect Instagram
- Create Content
- View Content
- Schedule
- Start Autopilot
- Pause Autopilot

## 1.6 Instagram Connection

The dashboard shall contain:

> **Connect Instagram**

When clicked, the frontend shall request an Instagram authorization URL from the backend.

The backend shall initiate the appropriate Meta/Instagram OAuth process.

The user shall then be redirected to the official Meta/Instagram authorization page.

The user shall authenticate and authorize the application.

The user shall never manually provide:

- Instagram access token
- Facebook access token
- OAuth authorization code
- Client secret
- Instagram account ID

The backend shall handle these automatically.

## 1.7 OAuth Callback

The backend shall provide a secure OAuth callback route.

Example:

```
/api/auth/instagram/callback
```

The exact route may be changed by the developer.

The callback shall:

1. Receive the authorization response.
2. Validate the OAuth state.
3. Validate the authorization code.
4. Exchange credentials where required.
5. Obtain the required access token.
6. Retrieve the Instagram account.
7. Verify the account.
8. Store credentials securely.
9. Associate the Instagram account with the logged-in platform user.
10. Redirect the user back to the dashboard.

## 1.8 Token Management

Access tokens shall be completely hidden from the user.

The backend shall manage:

- Token acquisition
- Token exchange
- Token storage
- Token validation
- Expiration detection
- Refresh / reconnection where supported
- Permission validation

Restrictions:

- Tokens shall never be displayed in the frontend.
- Tokens shall never be stored in browser local storage.
- Tokens shall never appear in public URLs.
- Tokens shall never be included in normal application logs.

## 1.9 Instagram Account Verification

After OAuth completion, the backend shall verify:

- Instagram account ID
- Username
- Account type
- Account availability
- Required permissions
- Publishing capability
- Token validity

Only supported Instagram Professional accounts shall be marked as ready for automated publishing.

## 1.10 Successful Connection

After successful verification, the user shall automatically return to the dashboard.

The dashboard shall show:

> **Instagram Connected ✓**

It shall display:

- Instagram username
- Profile picture where available
- Account type
- Connection status
- Last verification time

The Connect button shall change to account management controls.

**Available controls:**

- Manage
- Reconnect
- Verify
- Disconnect

## 1.11 Disconnect

Users shall be able to disconnect Instagram.

When disconnected:

- Autopublishing shall stop.
- Future publishing jobs shall be paused / cancelled safely.
- Credentials shall be removed or invalidated according to the security implementation.
- Historical records shall remain.
- Published content history shall remain.
- The dashboard shall return to the disconnected state.

Previously published Instagram posts shall not be deleted automatically.

---

# Chapter 2 — AI Content Engine and Content Generation

## 2.1 AI Provider

The primary AI provider shall use:

[https://combined-alidia-suhailtechlnfo-01b0509f.koyeb.app](https://combined-alidia-suhailtechlnfo-01b0509f.koyeb.app)

The provider shall be integrated through a dedicated backend AI service.

The frontend shall never communicate directly with the AI provider when credentials or sensitive configuration are involved.

## 2.2 AI Capability

The primary AI provider is text-only.

Therefore, the system shall use the AI for intelligence and text generation rather than expecting it to generate:

- Images
- Videos
- Voice
- Music
- Audio

The AI shall generate instructions and text that other platform components can use.

## 2.3 AI Responsibilities

The AI shall generate:

- Content ideas
- Topics
- Hooks
- Captions
- Hashtags
- Calls to action
- Educational posts
- Promotional posts
- Inspirational posts
- Storytelling posts
- Engagement posts
- Carousel text
- Reel scripts
- On-screen text
- Questions
- Quotes
- Content variations

## 2.4 Brand Configuration

Each user shall have configurable brand instructions.

Settings shall include:

- Brand name
- Brand description
- Target audience
- Industry
- Tone
- Personality
- Writing style
- Preferred language
- Preferred CTA
- Preferred hashtag style
- Words to use
- Words to avoid
- Topics to avoid
- Caption length
- Content categories

The AI shall use these settings when generating content.

## 2.5 Content Categories

The system shall support categories such as:

- Educational
- Promotional
- Inspirational
- Storytelling
- Community
- Engagement
- Product / service
- Tips
- Quotes
- News / commentary
- Behind-the-scenes
- General

Users shall be able to enable or disable categories.

## 2.6 AI Prompt Engine

The backend shall construct prompts dynamically.

A prompt may contain:

```
Brand information
+ Target audience
+ Brand voice
+ Content category
+ Topic
+ Platform
+ Post format
+ CTA requirements
+ Hashtag requirements
+ Previous content context
```

The AI shall then return structured content.

## 2.7 Structured AI Response

The application shall convert AI output into an internal content structure.

Example:

```json
{
  "content_type": "image",
  "category": "educational",
  "topic": "Example Topic",
  "hook": "Example Hook",
  "caption": "Example caption...",
  "hashtags": [
    "#example",
    "#education"
  ],
  "cta": "Follow for more",
  "visual_text": "Example visual text"
}
```

The exact structure shall be implemented by the developer but must contain enough information for downstream media and publishing processes.

## 2.8 Content Types

The platform shall support:

### Image

AI generates:

- Hook
- Visual text
- Caption
- CTA
- Hashtags

A template / media system creates the actual image.

### Carousel

AI generates multiple slides.

Example:

- Slide 1 — Hook
- Slide 2 — Main Point
- Slide 3 — Main Point
- Slide 4 — Main Point
- Slide 5 — CTA

### Reel

AI generates:

- Hook
- Script
- Scene instructions
- On-screen text
- Caption
- Hashtags
- CTA

The actual video shall come from an uploaded video, existing media, template, or supported media-generation pipeline.

### Existing Media

The user can provide an existing image / video.

The AI only generates:

- Caption
- Hashtags
- CTA
- Description
- Supporting text

## 2.9 AI Generation Modes

The system shall support:

### Automatic Mode

The AI automatically creates content according to the user's strategy and schedule.

### Approval Mode

AI generates content and saves it as a draft. The user reviews it before publication.

### Manual Mode

The user manually requests content generation.

## 2.10 Regeneration

Users shall be able to click:

> **Regenerate**

The AI shall generate a new version while respecting the same brand settings.

Users may also request changes such as:

- Make shorter
- Make longer
- Make more professional
- Make more engaging
- Change hook
- Change CTA
- Change hashtags
- Rewrite caption

## 2.11 Duplicate Prevention

The system shall compare new content with previous content.

Checks shall include:

- Caption similarity
- Topic similarity
- Hook similarity
- Hashtag similarity
- Content hash
- Media hash

If content is too similar, the system shall regenerate it.

## 2.12 AI Failure Handling

If the AI provider fails:

1. Record the error.
2. Retry according to configuration.
3. Do not publish incomplete content.
4. Keep the scheduled task pending.
5. Retry later.
6. Notify the user if the failure becomes permanent.

---

# Chapter 3 — Media, Templates, Scheduling and Content Management

## 3.1 Text-Only AI Media Strategy

Because the primary AI provider generates text only, the platform shall have an independent media system.

Media may come from:

- User uploads
- Existing media library
- Predefined templates
- Stock media integrations
- External media-generation services
- Existing videos
- Existing music / video assets

The AI shall determine what type of media is required.

## 3.2 Media Library

Each user shall have a media library.

The library shall support:

- Images
- Videos
- Audio where required by supported workflows
- Generated graphics
- Templates
- Brand assets

Each media item shall contain:

| Field | Description |
| --- | --- |
| Media ID | Unique identifier |
| User ID | Owning user |
| File type | Image, video, audio, etc. |
| File URL / storage reference | Storage location |
| Dimensions | Width × height |
| File size | Size in bytes |
| Creation date | When created |
| Status | Current state |

## 3.3 Image Templates

The platform shall support reusable image templates.

Templates may include:

- Logo
- Headline
- Supporting text
- CTA
- Username
- Website
- Background
- Image area
- Decorative elements

The AI supplies the content while the template engine creates the visual.

## 3.4 Carousel Templates

Carousel templates shall allow the system to automatically render multiple slides.

The system shall:

1. Receive AI slide content.
2. Select the configured template.
3. Render each slide.
4. Validate each image.
5. Store the final slides.
6. Prepare the carousel publishing job.

## 3.5 Content Calendar

The system shall provide a visual content calendar.

Users shall configure:

- Posting days
- Posting times
- Timezone
- Posts per day
- Content categories
- Content types
- Minimum time between posts

Example:

| Day | Category |
| --- | --- |
| Monday | Educational |
| Tuesday | Engagement |
| Wednesday | Educational |
| Thursday | Storytelling |
| Friday | Promotional |
| Saturday | Community |
| Sunday | Flexible |

## 3.6 Content Queue

The system shall maintain a queue containing:

- Drafts
- Approved posts
- Scheduled posts
- Processing posts
- Publishing posts
- Published posts
- Failed posts

Each content item shall have a unique ID.

## 3.7 Content Status

Supported statuses shall include:

- `DRAFT`
- `GENERATING`
- `GENERATED`
- `REVIEW_REQUIRED`
- `APPROVED`
- `SCHEDULED`
- `PROCESSING`
- `PUBLISHING`
- `PUBLISHED`
- `FAILED`
- `REJECTED`
- `CANCELLED`

## 3.8 Approval Workflow

In approval mode:

```
AI Generation
     ↓
Draft
     ↓
User Review
     ↓
Approve
     ↓
Schedule
     ↓
Publish
```

The user shall be able to:

- Edit
- Regenerate
- Replace media
- Change caption
- Change hashtags
- Reschedule
- Approve
- Reject
- Delete

## 3.9 Automatic Workflow

In automatic mode:

```
AI Generation
     ↓
Validation
     ↓
Media Preparation
     ↓
Schedule
     ↓
Instagram Publishing
```

No manual approval shall be required.

## 3.10 Scheduler

A backend scheduler shall continuously monitor scheduled content.

For every due post, it shall:

1. Find the content.
2. Lock the publishing job.
3. Validate the content.
4. Validate the media.
5. Validate the Instagram connection.
6. Send the content to the publishing queue.
7. Publish.
8. Verify the result.
9. Update the content status.

The scheduler shall prevent two workers from publishing the same content simultaneously.

## 3.11 Queue Architecture

The system should use separate processing stages:

```
AI Generation Queue
        ↓
Validation Queue
        ↓
Media Processing Queue
        ↓
Instagram Publishing Queue
        ↓
Publishing Verification Queue
```

This architecture shall prevent one failed operation from blocking unrelated content.

## 3.12 Media Validation

Before Instagram publishing, the system shall validate:

- File existence
- File accessibility
- File format
- File size
- Dimensions
- Media type
- Required public accessibility
- Instagram compatibility

Invalid media shall stop the publishing job.

## 3.13 Content Preview

Before publishing, users shall see:

- Media preview
- Instagram-style preview
- Caption
- Hashtags
- CTA
- Scheduled time
- Content type
- Account that will receive the post

## 3.14 Manual Publish

Users shall be able to select eligible content and choose:

> **Publish Now**

The system shall perform all normal validation before sending the publishing request.

## 3.15 Pause and Resume

Users shall be able to:

> **Pause Autopilot**

When paused:

- New publishing jobs shall not start.
- Existing content shall remain stored.
- Scheduled content shall remain scheduled unless the user chooses otherwise.
- AI generation may optionally continue.

When resumed, the scheduler shall continue processing eligible content.

---

# Chapter 4 — Instagram API Publishing, Security and Automation

## 4.1 Official Instagram API

All automated Instagram publishing shall use the official Meta/Instagram API.

The application shall **not** use:

- Instagram password automation
- Browser scraping
- Unofficial login automation
- Fake API endpoints
- User password storage

The platform shall only perform operations supported by the official API and the permissions granted to the application.

## 4.1b Web Search Integration (Tavily)

The platform shall use [https://app.tavily.com](https://app.tavily.com) (Tavily API) for web searching in order to get more accurate, up-to-date information for content generation and research.

The integration shall:

- Be handled through a dedicated backend search service, never directly from the frontend.
- Allow the AI prompt engine to enrich prompts with current facts, trends, and references retrieved via web search.
- Store the Tavily API key in environment variables (see Section 4.11), never in frontend code or version-controlled secrets.

The Tavily base URL and configuration:

```env
TAVILY_BASE_URL=https://app.tavily.com
TAVILY_API_KEY=...
```

### Backup Web Search Providers

The platform shall maintain backup web search providers so that search functionality remains available if the primary provider is unavailable. The backend search service shall support automatic fallback in the following priority order:

| Priority | Provider | Base URL | Authentication | Notes |
| --- | --- | --- | --- | --- |
| 1 (Primary) | Tavily | `https://app.tavily.com` | API key | Primary provider for accurate, up-to-date search results |
| 2 (Backup) | DuckDuckGo Instant Answer | `https://api.duckduckgo.com` | No API key required | Lightweight, privacy-focused, instant answers |
| 3 (Backup) | Serper | `https://serper.dev` | API key | Google-powered search results |

#### Backup 1 — DuckDuckGo Instant Answer API

DuckDuckGo's Instant Answer API stands out for its simplicity and privacy focus, delivering quick search results without requiring an API key. It is ideal for lightweight AI agents needing fast, no-authentication queries. It returns structured data such as abstracts, definitions, and related topics from over 100 sources.

Key features and limits:

- **No API key required** — instant access.
- **Rate limit** — approximately 60 requests per minute.
- **Response format** — JSON with topics, abstracts, and images.

Practical integration example:

```python
import requests

def duckduckgo_search(query):
    url = f"https://api.duckduckgo.com/?q={query}&format=json&no_html=1&skip_disambig=1"
    response = requests.get(url)
    return response.json()

result = duckduckgo_search("latest AI advancements")
print(result.get('AbstractText', 'No abstract available'))
```

#### Backup 2 — Serper

The platform may fall back to [Serper](https://serper.dev) (Google-powered search API) when the primary provider and DuckDuckGo are unavailable.

Configuration:

```env
SERPER_BASE_URL=https://serper.dev
SERPER_API_KEY=...
```

#### Fallback Behavior

The backend search service shall:

1. Attempt the primary provider (Tavily) first.
2. On failure or unavailability, automatically fall back to DuckDuckGo Instant Answer.
3. If DuckDuckGo is also unavailable, fall back to Serper.
4. If all providers fail, record the failure, keep the generation task pending, and retry later according to the failure handling rules (Section 2.12).
5. Log every provider switch and failure in the AI logs (Section 4.12).

## 4.2 Publishing Architecture

The Instagram service shall be isolated from the rest of the application.

Recommended service structure — `InstagramService`:

```
connectAccount()
verifyAccount()
getAccount()
createMediaContainer()
checkMediaStatus()
publishMedia()
getPublishingStatus()
getInsights()
disconnectAccount()
```

The exact API implementation shall follow Meta's current official documentation and API requirements.

## 4.3 Image Publishing

For an image post, the workflow shall be:

```
Approved Content
      ↓
Image Validation
      ↓
Public Media URL
      ↓
Instagram Media Container
      ↓
Container Processing
      ↓
Publish
      ↓
Verify
      ↓
Save Instagram Media ID
```

The system shall not mark the post as successfully published merely because the initial API request succeeded.

## 4.4 Carousel Publishing

For carousel content:

```
Carousel Slides
      ↓
Validate Every Slide
      ↓
Create Child Media Containers
      ↓
Create Carousel Container
      ↓
Check Processing
      ↓
Publish
      ↓
Verify
```

Every child media item shall be validated before the final carousel publishing request.

## 4.5 Reel Publishing

For Reel content:

```
Video
  ↓
Validate Video
  ↓
Prepare Public Media URL
  ↓
Create Reel Container
  ↓
Monitor Processing
  ↓
Publish
  ↓
Verify
```

The actual supported Reel publishing parameters shall be implemented according to the current official Meta/Instagram API.

## 4.6 Publishing Verification

The system shall verify the result after attempting publication.

The final content record shall contain:

- Instagram media ID
- Publishing status
- Published timestamp
- API response status
- Error information where applicable

**Successful result:** `PUBLISHED`

**Failure:** `FAILED`

## 4.7 Retry System

Temporary errors shall use automatic retries.

Example:

```
Attempt 1
   ↓
Failure
   ↓
Backoff
   ↓
Attempt 2
   ↓
Failure
   ↓
Backoff
   ↓
Attempt 3
   ↓
Permanent Failure
```

Authentication or permission errors shall not be endlessly retried.

## 4.8 Duplicate Publishing Protection

Every publishing job shall have a unique ID.

Before publishing, the backend shall check:

- Content ID
- Publishing status
- Existing Instagram media ID
- Active job lock
- Previous publishing attempts

If a post has already been successfully published, the system shall never publish it again automatically.

## 4.9 Token Security

Instagram credentials shall be stored only on the backend.

The system shall use:

- HTTPS
- Secure database storage
- Encryption where appropriate
- Environment variables
- Secret management
- Access control
- Audit logs

The frontend shall never receive raw access tokens.

## 4.10 OAuth Security

OAuth implementation shall include:

- Secure redirect URI
- State validation
- Secure callback
- CSRF protection
- Token validation
- Permission validation
- Error handling

OAuth credentials shall never be hardcoded into frontend source code.

## 4.11 Environment Configuration

Sensitive values shall be stored in environment variables.

Example:

```env
APP_URL=https://instagram.senseiphoenix.name.ng
AI_PROVIDER_BASE_URL=https://combined-alidia-suhailtechlnfo-01b0509f.koyeb.app
AI_PROVIDER_API_KEY=...
TAVILY_BASE_URL=https://app.tavily.com
TAVILY_API_KEY=...
META_APP_ID=...
META_APP_SECRET=...
META_REDIRECT_URI=...
DATABASE_URL=...
ENCRYPTION_KEY=...
```

This includes, at minimum:

| Variable | Purpose |
| --- | --- |
| `APP_URL` | Platform domain |
| `AI_PROVIDER_BASE_URL` / `AI_PROVIDER_API_KEY` | Text AI provider URL and key |
| `TAVILY_BASE_URL` / `TAVILY_API_KEY` | Tavily AI web search URL and key |
| `META_APP_ID` / `META_APP_SECRET` / `META_REDIRECT_URI` | Meta/Instagram OAuth credentials |
| `DATABASE_URL` | Database connection |
| `ENCRYPTION_KEY` | Encryption of stored access tokens |

Actual secrets shall never be committed to GitHub or exposed in frontend code.

## 4.12 Database Architecture

The database shall contain, at minimum, logical records for:

### Users

| Field | Description |
| --- | --- |
| `id` | Unique identifier |
| `email` | User email |
| `password_hash` | Hashed password |
| `email_verified` | Verification flag |
| `created_at` | Creation timestamp |
| `updated_at` | Update timestamp |

### Instagram Accounts

| Field | Description |
| --- | --- |
| `id` | Unique identifier |
| `user_id` | Owning user |
| `instagram_user_id` | Instagram account ID |
| `username` | Instagram username |
| `account_type` | Professional account type |
| `encrypted_access_token` | Encrypted access token |
| `token_status` | Token state |
| `permissions` | Granted permissions |
| `connected_at` | Connection timestamp |
| `last_verified_at` | Last verification timestamp |
| `created_at` | Creation timestamp |
| `updated_at` | Update timestamp |

### Content

| Field | Description |
| --- | --- |
| `id` | Unique identifier |
| `user_id` | Owning user |
| `instagram_account_id` | Target account |
| `content_type` | Image / carousel / reel / existing media |
| `category` | Content category |
| `topic` | Content topic |
| `hook` | Post hook |
| `caption` | Post caption |
| `hashtags` | Hashtag list |
| `cta` | Call to action |
| `media_id` | Associated media |
| `status` | Content status |
| `scheduled_at` | Scheduled time |
| `published_at` | Publishing time |
| `instagram_media_id` | Published media ID |
| `created_at` | Creation timestamp |
| `updated_at` | Update timestamp |

### Publishing Jobs

| Field | Description |
| --- | --- |
| `id` | Unique identifier |
| `content_id` | Associated content |
| `instagram_account_id` | Target account |
| `status` | Job status |
| `attempts` | Retry count |
| `last_error` | Last error message |
| `started_at` | Start timestamp |
| `completed_at` | Completion timestamp |
| `created_at` | Creation timestamp |
| `updated_at` | Update timestamp |

### AI Logs

| Field | Description |
| --- | --- |
| `id` | Unique identifier |
| `user_id` | Owning user |
| `content_id` | Associated content |
| `provider` | AI provider name |
| `model` | Model used |
| `status` | Request status |
| `request_time` | Request timestamp |
| `response_time` | Response timestamp |
| `error` | Error details |
| `created_at` | Creation timestamp |

## 4.13 Audit Logs

Important actions shall be logged.

Examples:

- Account creation
- Login
- Instagram connection
- Instagram disconnection
- Token update
- Content generation
- Content approval
- Content rejection
- Content publishing
- Publishing failure
- Autopilot activation
- Autopilot pause

## 4.14 Emergency Stop

A prominent control shall allow the user to immediately stop automation.

Button:

> **Pause Autopilot**

The system shall prevent new publishing jobs from starting.

A global administrative emergency stop may also be implemented.

---

# Chapter 5 — Dashboard, Administration, Monitoring and Complete System Workflow

## 5.1 Main Dashboard

The dashboard shall provide a complete overview.

**Top section:**

> Instagram Account — Connected ✓ — @username

**Autoposter section:**

> AUTOPILOT — ● ACTIVE

**Quick controls:**

- Pause
- Resume
- Create Post
- View Queue
- Schedule
- Settings

## 5.2 Dashboard Statistics

The dashboard shall display:

- Total posts
- Published posts
- Scheduled posts
- Drafts
- Failed posts
- Posts today
- Posts this week
- Posts this month
- AI generations
- AI failures

Where supported, Instagram performance data may also be displayed.

## 5.3 Content Management

The Content page shall provide tabs:

- All
- Drafts
- Scheduled
- Published
- Failed
- Rejected

Each post shall display:

- Preview
- Caption
- Content type
- Category
- Status
- Scheduled time
- Published time
- Instagram account
- Actions

## 5.4 Content Actions

Depending on status, users shall be able to:

- View
- Edit
- Regenerate
- Approve
- Reject
- Schedule
- Reschedule
- Publish Now
- Cancel
- Delete
- Retry

## 5.5 Calendar Interface

The calendar shall display scheduled posts.

Users shall be able to:

- View posts by day
- View posts by week
- View posts by month
- Click a post
- Edit a post
- Reschedule by changing date / time
- Create new scheduled content

The calendar shall respect the user's configured timezone.

## 5.6 AI Settings

The AI Settings page shall allow users to configure:

- AI model
- Brand voice
- Tone
- Audience
- Content categories
- Caption length
- Hashtag strategy
- CTA
- Words to avoid
- Topics to avoid
- Generation mode

The AI provider base URL shall be managed by the system / backend rather than exposed as a normal user setting.

## 5.7 Posting Settings

Users shall configure:

- Posts per day
- Posting days
- Posting times
- Timezone
- Content types
- Content categories
- Automatic generation
- Automatic publishing
- Approval requirement
- Retry attempts

## 5.8 Instagram Settings

The Instagram settings page shall display:

- Connected account
- Username
- Account type
- Connection status
- Last verification
- Reconnect
- Disconnect
- Verify Connection

Raw access tokens shall never be displayed.

## 5.9 Internal Notifications

The system shall notify users about important events using **internal notifications only** (in-app notification center).

The platform shall **not** use external email delivery (no SMTP or third-party email services). All notifications shall be displayed within the application via a notification center (bell icon) and, where applicable, browser push notifications.

Notifications may include:

- Instagram successfully connected
- Instagram connection failed
- Token requires attention
- Content generated
- Content awaiting approval
- Post successfully published
- Post failed
- Autopilot paused
- Autopilot resumed
- AI provider unavailable

Each notification shall contain a title, message, timestamp, read/unread status, and a link to the related content or action.

## 5.10 Error Center

The platform shall include an error / activity center.

It shall display:

- Error type
- Content affected
- Date / time
- Error message
- Retry count
- Current status
- Recommended action

Users shall be able to retry eligible failed jobs.

## 5.11 Admin Panel

A future / admin interface shall provide global control over the system.

Admin capabilities shall include:

- View users
- View connected Instagram accounts
- View active autoposters
- Disable accounts
- View AI usage
- View publishing jobs
- View failed jobs
- Retry jobs
- Pause global publishing
- Manage AI configuration
- Manage prompts
- Manage templates
- View system logs
- View API errors
- Monitor system health

## 5.12 System Health Monitoring

The backend shall monitor:

- AI provider availability
- AI response time
- Database health
- Queue health
- Scheduler health
- Instagram API responses
- Publishing failures
- OAuth failures
- Token failures

A system health dashboard shall indicate:

```
AI Provider       ✓ Operational
Database          ✓ Operational
Scheduler         ✓ Operational
Publishing Queue  ✓ Operational
Instagram API     ✓ Operational
```

## 5.13 Complete Automated Workflow

The complete system shall operate as follows:

```
USER
 ↓
Landing Page
 ↓
Create Account / Login
 ↓
Dashboard
 ↓
Connect Instagram
 ↓
Official Instagram/Meta Authorization
 ↓
OAuth Callback
 ↓
Backend Token Processing
 ↓
Instagram Account Verification
 ↓
Instagram Connected
 ↓
User Configures Brand
 ↓
User Configures Content Strategy
 ↓
User Configures Schedule
 ↓
Start Autopilot
 ↓
Scheduler Detects Upcoming Content
 ↓
Content Planner Selects Topic
 ↓
AI Prompt Engine Builds Prompt
 ↓
AI Provider Generates Text
 ↓
AI Response Validation
 ↓
Duplicate Check
 ↓
Content Approved Automatically or Manually
 ↓
Media Selected/Created
 ↓
Media Validation
 ↓
Publishing Queue
 ↓
Instagram Media Container
 ↓
Instagram Processing
 ↓
Instagram Publish
 ↓
Publishing Verification
 ↓
Instagram Media ID Stored
 ↓
Content Marked PUBLISHED
 ↓
Analytics Updated
 ↓
Activity Logged
 ↓
Next Scheduled Content
```

## 5.14 Failure Workflow

If any stage fails:

```
Operation
   ↓
Failure
   ↓
Classify Error
   ↓
Temporary?
 ┌─YES──────────────┐
 ↓                  │
Retry               │
 ↓                  │
Success             │
                    │
NO                  │
 ↓                  │
Mark Failed         │
 ↓                  │
Log Error           │
 ↓                  │
Notify User         │
```

The system shall never publish incomplete or invalid content.

## 5.15 User Experience Requirement

The entire platform shall feel simple to the end user.

The user should not need to understand how the underlying system works.

The intended experience is:

1. Visit [instagram.senseiphoenix.name.ng](https://instagram.senseiphoenix.name.ng).
2. Create an account or log in.
3. Click "Connect Instagram".
4. Authorize the application on Instagram / Meta.
5. Return automatically to the dashboard.
6. Configure what type of content they want.
7. Configure how frequently they want posts.
8. Click "Start Autopilot".
9. The AI generates the content.
10. The system prepares the media.
11. The system schedules the content.
12. The Instagram API publishes it.
13. The system confirms publication.
14. The system repeats the process automatically.

## 5.16 Core Technical Principle

The platform shall maintain a strict separation between:

> **AI Intelligence** and **Media + Publishing Infrastructure**

The AI provider at [https://combined-alidia-suhailtechlnfo-01b0509f.koyeb.app](https://combined-alidia-suhailtechlnfo-01b0509f.koyeb.app) shall primarily handle text intelligence and content generation.

The application shall handle:

- User authentication
- Instagram OAuth
- Token management
- Brand configuration
- Content planning
- Scheduling
- Media management
- Templates
- Media processing
- Instagram API integration
- Publishing
- Verification
- Retry handling
- Database storage
- Logging
- Analytics
- Security
- Notifications
- Administration

## 5.17 Final Product Requirement

The finished application shall be a production-ready AI Instagram autopublishing platform available at:

[https://instagram.senseiphoenix.name.ng](https://instagram.senseiphoenix.name.ng)

The system shall provide a complete automated pipeline:

```text
Account → Instagram Connection → AI → Content → Media → Schedule → Instagram API → Published Post → Verification → Analytics
```

The system shall be built so that a user can connect their Instagram account through the normal official authorization flow without manually handling tokens or API credentials.

The system shall use the configured text-only AI provider for content intelligence while relying on the application's media / template infrastructure and official Instagram API for actual content publishing.

The architecture shall be modular, secure, queue-based, fault-tolerant, scalable, and designed so additional social platforms and additional AI / media providers can be integrated in future versions without requiring a complete rewrite of the platform.
---

# Chapter 6 — Non-Functional Requirements, Content Safety, Compliance and Analytics

## 6.1 Performance Requirements

The platform shall meet the following performance targets:

| Metric | Target |
| --- | --- |
| Landing page load time | ≤ 2 seconds |
| Dashboard load time | ≤ 3 seconds |
| Login / registration response | ≤ 2 seconds |
| AI content generation (per post) | ≤ 30 seconds typical |
| Web search enrichment | ≤ 10 seconds |
| Instagram publishing request | ≤ 15 seconds |
| Notification delivery (in-app) | Near real-time (≤ 5 seconds) |

The system shall be designed to support at least the expected initial concurrent user load and shall scale horizontally where supported by the deployment platform (see Chapter 8).

## 6.2 Instagram API Rate Limits and Quotas

The platform shall respect all Meta/Instagram API rate limits and publishing quotas.

The system shall:

- Track API usage per account and per time window.
- Throttle the publishing queue when limits approach.
- Queue excess requests instead of failing them.
- Back off automatically on rate-limit responses (HTTP 429).
- Never exceed the API's daily or hourly publishing limits.

## 6.3 Content Safety and Moderation

The platform shall never publish content that violates Instagram's Community Guidelines or the user's own brand rules.

Before publishing, the system shall screen generated content for:

- Hate speech and harassment
- Sexual or explicit content
- Violence and illegal content
- Spam-like behavior (excessive hashtags, repeated identical captions)
- Trademark or copyright misuse where detectable

Content that fails moderation shall be:

1. Marked as `REJECTED`.
2. Logged with the reason.
3. Not published.
4. Flagged to the user via internal notification.

The user shall be able to configure additional banned words and prohibited topics (see Section 2.4).

## 6.4 Privacy and Data Protection

The platform shall handle personal data responsibly:

- User credentials shall be hashed and never stored in plain text.
- Instagram access tokens shall be encrypted at rest.
- User personal data shall be accessible only to the owning user and administrators.
- Users shall be able to delete their account and personal data, which shall trigger removal of their credentials, content, and logs where technically possible.
- Historical published-post records shall be retained for the user's reference even after disconnection, unless the user requests deletion.
- Third-party APIs (AI provider, Tavily, Serper, Meta) shall only receive the minimum data required for each operation.

## 6.5 Analytics and Insights

The platform shall track performance data where the official API supports it.

**User-level analytics:**

- Total posts, published / scheduled / drafts / failed
- Posts today / this week / this month
- AI generations and failures
- Publishing success rate

**Instagram insights (where supported by the API):**

- Follower count trends
- Post reach and impressions
- Likes and comments
- Engagement rate

**System-level analytics (admin):**

- AI usage per user
- Publishing job volume and failure rates
- Queue depth and processing times
- Web search usage

Instagram insights data shall be stored in the database and displayed on the user dashboard where available.

## 6.6 Account and Edge-Case Handling

The platform shall handle the following edge cases gracefully:

- The user changes their Instagram password or revokes the application — the dashboard shall display "Instagram connection needs attention" with Reconnect as the primary action.
- The Instagram account goes private, is disabled, or loses Professional status — autopilot shall pause and the user shall be notified internally.
- The user disconnects mid-autopilot — all queued jobs shall be cancelled safely without publishing partial content.
- Daylight saving time or timezone changes — scheduled times shall be resolved against the user's stored timezone and adjusted safely.
- The AI provider returns an unexpected response format — the content shall be marked `FAILED`, logged, and retried.
- The media upload/storage fails — the job shall fail safely, be retried, and be shown in the Error Center.

## 6.7 Media Storage and Format Limits

Media files shall be stored in a backend storage service (e.g., S3-compatible object storage or the deployment platform's storage) behind a CDN where available.

Instagram media requirements shall be enforced before publishing:

| Media Type | Maximum | Notes |
| --- | --- | --- |
| Image (JPEG/PNG) | 1080 × 1350 px recommended | Square/landscape/portrait supported |
| Carousel images | 3–10 slides | Each slide validated individually |
| Video / Reel (MP4) | ≤ 60 seconds (Reels) | H.264, AAC audio |
| File size | Per Instagram API limits | Validated before upload |

Unsupported formats shall be rejected at the media validation stage with a clear message to the user.

## 6.8 Logging and Monitoring Stack

The backend shall maintain structured logs for:

- Application events (requests, errors, auth events)
- AI provider requests and responses (summarized, without full prompt content where sensitive)
- Web search requests and fallbacks
- Instagram API requests and responses (without tokens)
- Publishing jobs and queue events
- Scheduler ticks and job locks

Monitoring shall support:

- Error alerting for administrators
- Health check endpoints (`/health`) for the deployment platform
- Per-service status visibility on the admin dashboard

---

# Chapter 7 — API, Testing and Versioning

## 7.1 Backend API Conventions

The backend shall expose a RESTful API using the following conventions:

- JSON request and response bodies.
- Authentication via secure session cookies or Bearer tokens (bearer tokens for API clients only).
- Standard HTTP status codes (200, 201, 400, 401, 403, 404, 409, 422, 429, 500).
- Consistent error response format:

```json
{
  "error": {
    "code": "PUBLISHING_FAILED",
    "message": "Human-readable description",
    "details": {}
  }
}
```

- Rate limiting on authentication and publishing endpoints.
- Pagination for list endpoints (content, posts, logs, notifications).

## 7.2 Testing Requirements

The platform shall be developed with automated testing:

| Level | Coverage Target |
| --- | --- |
| Unit tests | Auth, validation, prompt building, queue logic, retry logic |
| Integration tests | OAuth flow, Instagram service, AI service, search service, scheduler |
| End-to-end tests | Registration → connect Instagram → generate → schedule → publish |
| AI output tests | Structured response validation, duplicate check, moderation |

Tests shall run automatically in the CI pipeline on every push and pull request.

## 7.3 SRS Versioning and Revision History

| Version | Date | Changes |
| --- | --- | --- |
| 1.0 | Aug 10, 2026 | Initial SRS: Chapters 1–5 |
| 1.1 | Aug 10, 2026 | Full Chapter 5; Tavily web search (4.1b); backup search providers (DuckDuckGo, Serper); expanded environment variables; signup without email verification; internal-only notifications; Chapters 6–8 (non-functional, compliance, analytics, deployment, admin pricing) |

---

# Chapter 8 — Deployment, Admin Panel and Pricing

## 8.1 Supported Deployment Platforms

The platform shall be deployable on the following cloud platforms without requiring a rewrite:

| Platform | Frontend / Backend Support | Notes |
| --- | --- | --- |
| [Koyeb](https://www.koyeb.com) | Backend services, workers, scheduled tasks | AI provider already hosted here; secret env vars via Koyeb dashboard |
| [Render](https://render.com) | Web services, background workers, cron jobs, Postgres | Static site hosting for frontend; env vars via Render dashboard |
| [Railway](https://railway.app) | Services, Postgres, Redis, cron | Env vars via Railway dashboard; simple scaling |

Deployment requirements:

- All secrets (see Section 4.11) shall be configured as environment variables on the deployment platform, never committed to the repository.
- The platform shall use a `.env.example` file (without real values) as the local development template.
- The scheduler, queue workers, and web server shall be runnable as separate processes so they can be scaled independently on any of the three platforms.
- Health check endpoints shall be exposed so the platform's uptime monitoring (Koyeb health checks, Render uptime, Railway monitoring) works out of the box.
- A `Procfile` / platform configuration shall define process types (web, worker, scheduler).

## 8.2 Admin Subdomain

The administration panel shall be hosted at:

```
https://admin-instagram.senseiphoenix.name.ng
```

The admin panel shall be a separate application/module with its own authentication and role checks. Normal platform users shall not be able to access it.

## 8.3 Admin Dashboard and Capabilities

The admin dashboard shall provide global control over the system:

- View, search, and filter users
- View connected Instagram accounts and their status
- View active autoposters
- Disable / enable user accounts
- View AI usage per user and in total
- View publishing jobs, including failed jobs
- Retry failed jobs
- Pause global publishing
- Manage AI configuration (provider URL, model selection, prompt templates)
- Manage web search configuration (Tavily, DuckDuckGo, Serper)
- Manage templates and media assets
- View system logs and API errors
- Monitor system health
- Manage pricing and subscription plans (see Section 8.4)

## 8.4 Pricing and Subscription Management

The admin shall be able to define and manage pricing plans from the admin dashboard.

A pricing plan shall include:

| Field | Description |
| --- | --- |
| Plan name | e.g., Free, Starter, Pro |
| Price | Amount and currency |
| Billing period | Monthly / yearly |
| Instagram accounts allowed | Number of connected accounts |
| Posts per month | Maximum published posts |
| Posts per day | Maximum automated daily posts |
| AI generations | Maximum AI generations per month |
| Web search queries | Maximum search enrichments per month |
| Content types | Image / carousel / reel availability |
| Template access | Free / premium template tiers |
| Storage quota | Media library size limit |
| Status | Active / archived |

The system shall enforce plan limits automatically:

- When a user exceeds their plan limits, generation and publishing shall be paused and the user shall be notified internally.
- The dashboard shall display the user's current plan, usage counters, and remaining quota.
- Plan changes by the admin shall take effect on the user's next billing cycle or immediately, as configured.

A future billing/checkout integration may be added, but pricing configuration itself shall be fully manageable by the admin without code changes.

## 8.5 Deployment Workflow

The recommended deployment workflow shall be:

1. Push code to the GitHub repository (`main` branch).
2. CI pipeline runs tests and linting on every push / pull request.
3. The deployment platform (Koyeb / Render / Railway) auto-deploys from `main` or a tagged release.
4. Health checks confirm the new version before routing traffic.
5. Database migrations are applied automatically or via a one-off deploy job.
6. If the new version fails health checks, the platform rolls back to the previous deployment.

---

# Final System Summary

The finished application shall be a production-ready AI Instagram autopublishing platform available at:

[https://instagram.senseiphoenix.name.ng](https://instagram.senseiphoenix.name.ng)

with administration at:

[https://admin-instagram.senseiphoenix.name.ng](https://admin-instagram.senseiphoenix.name.ng)

The complete automated pipeline remains:

```text
Account → Instagram Connection → AI → Content → Media → Schedule → Instagram API → Published Post → Verification → Analytics
```

The system shall be modular, secure, queue-based, fault-tolerant, scalable, and designed so additional social platforms, additional AI providers, additional web search providers, and additional media providers can be integrated in future versions without requiring a complete rewrite of the platform.

# SRS — PHOENIX AI INSTAGRAM AUTOPUBLISHER

| Item | Value |
| --- | --- |
| **Platform Domain** | [https://instagram.senseiphoenix.name.ng](https://instagram.senseiphoenix.name.ng) |
| **AI Provider Base URL** | [https://combined-alidia-suhailtechlnfo-01b0509f.koyeb.app](https://combined-alidia-suhailtechlnfo-01b0509f.koyeb.app) |
| **Platform Type** | AI-powered Instagram content generation, scheduling, and automatic publishing system |
| **Primary AI Capability** | Text generation |
| **Primary Publishing Integration** | Official Meta/Instagram API |

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
- Email verification
- Secure session creation

The system shall validate:

- Email format
- Password requirements
- Duplicate email
- Required fields

After successful registration, the user shall be authenticated automatically after verification where appropriate.

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
META_APP_ID=...
META_APP_SECRET=...
META_REDIRECT_URI=...
DATABASE_URL=...
ENCRYPTION_KEY=...
```

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

*(Section content to be provided.)*

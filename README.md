GATE CSE 2027 Study HQ

A personal study management and progress-tracking web application designed to help organize and monitor preparation for the GATE Computer Science and Information Technology (CSE) examination.

🌐 Live Website: https://adhi0068.github.io/gate-study-hq/

Overview

GATE Study HQ is a web-based study tracker that helps manage the GATE CSE syllabus, track topic-wise progress, monitor PYQ completion, and keep study progress organized.

The application uses GitHub Pages for website hosting and Supabase for cloud database storage and authentication.

This separation allows the website code and study data to be maintained independently.

Features

- Syllabus Management: Organize subjects, topics, and subtopics.
- Study Progress Tracking: Mark individual subtopics as completed.
- PYQ Tracking: Track Previous Year Questions (PYQs) separately from study completion.
- Subject Status: Automatically organize subjects according to their study and PYQ completion status.
- Progress Dashboard: Monitor completed subtopics and other study statistics.
- Bulk Completion: Update multiple topic or PYQ statuses efficiently.
- Cloud Synchronization: Save and retrieve study progress using Supabase.
- Authentication: Sign in to access your personal cloud-saved progress.
- Cross-Browser Access: Access synchronized progress from different browsers and devices.
- Backup Support: Export study data for an additional backup.

Technology Stack

Technology| Purpose
HTML| Website structure
CSS| Styling and layout
JavaScript| Application logic and interactions
GitHub| Source code repository
GitHub Pages| Website hosting
Supabase Auth| User authentication
Supabase PostgreSQL| Cloud database
Supabase API| Communication between the website and database
Row Level Security (RLS)| Database access control

System Architecture

The project uses a client-side web application architecture.

                  USER
                    |
                    v
              WEB BROWSER
                    |
                    v
              GITHUB PAGES
              Website Hosting
                    |
             Loads Website Files
                    |
                    v
             HTML / CSS / JS
              Runs in Browser
                    |
                    | HTTPS API Requests
                    |
                    v
                SUPABASE
                    |
          +---------+----------+
          |                    |
          v                    v
      SUPABASE AUTH       POSTGRESQL
      Authentication     Cloud Database
                               |
                               v
                         study_data
                         User Progress

How the Architecture Works

1. GitHub Repository

Stores the application's source code, including the HTML, CSS, and JavaScript.

2. GitHub Pages

Hosts the website and makes it accessible through a public URL.

3. Browser

Downloads and executes the application code. It handles user interactions and communicates with Supabase.

4. Supabase Authentication

Authenticates users before allowing access to their personal cloud data.

5. Supabase Database

Stores the user's study progress in a PostgreSQL table named "study_data".

6. Row Level Security (RLS)

Ensures that authenticated users can access only the database records permitted by their user ID.

How Cloud Synchronization Works

The application follows this process:

1. The user opens the website hosted on GitHub Pages.
2. The browser loads the application.
3. The application connects to the Supabase project.
4. The user signs in through Supabase Authentication.
5. The application retrieves the user's saved progress from the database.
6. When study progress changes, the application sends updated data to Supabase.
7. Supabase checks the user's permissions through RLS policies.
8. The updated progress is saved in the cloud.

When the user opens the website on another browser or device and signs in using the same account, the application retrieves the previously saved progress.

Important: GitHub Pages does not store the user's study progress. Supabase handles cloud data storage independently.

Database Structure

The application uses a PostgreSQL table:

"public.study_data"

Column| Data Type| Description
"user_id"| UUID| User identifier linked to Supabase Auth
"data"| JSONB| Stores the user's study progress
"updated_at"| TIMESTAMPTZ| Records the last update time

The "user_id" column is the primary key and references "auth.users(id)".

The JSONB column stores the study tracker data, allowing the application to maintain structured progress information.

Security

The project uses Supabase Row Level Security (RLS) to protect user data.

- RLS is enabled on the "study_data" table.
- Database policies restrict access using "auth.uid()".
- Users must authenticate to access their personal cloud data.
- The Supabase publishable key is used by the browser application.
- Secret and service-role keys must never be exposed in client-side code.

Note: The GitHub repository and website source code are publicly accessible. Database access is separately controlled through Supabase Authentication and RLS policies.

Project Deployment

The application is deployed using GitHub Pages.

Deployment Steps

1. Upload the website files to the GitHub repository.
2. Open the repository's Settings.
3. Navigate to Pages.
4. Select the deployment branch and root folder.
5. Save the configuration.
6. Open the generated GitHub Pages URL.

Changes pushed to the configured branch are published through GitHub Pages.

Supabase Configuration

To configure cloud synchronization:

1. Create a Supabase project.
2. Create the "study_data" table with the required schema.
3. Enable Row Level Security.
4. Configure user-specific SELECT, INSERT, UPDATE, and DELETE policies.
5. Configure Supabase Authentication.
6. Add the Supabase project URL and publishable key to the application configuration.

Never add a service-role key or database password to the public repository.

Project Structure

gate-study-hq/
│
├── index.html       # Main application
└── README.md        # Project documentation

Additional files may be added as the application grows.

Future Improvements

Potential improvements include:

- Study timetable and daily targets.
- Revision scheduling and reminders.
- Mock test performance tracking.
- Subject-wise accuracy and performance analytics.
- Study streaks and consistency tracking.
- Enhanced progress reports.
- Additional backup and recovery options.

Live Application

GATE CSE 2027 Study HQ

https://adhi0068.github.io/gate-study-hq/

---

Built to make GATE CSE 2027 preparation more organized, measurable, and consistent.

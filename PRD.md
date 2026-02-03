# 📘 Product Requirements Document (PRD)

**Product:** Pursuit Student Dashboard – Weekly Curriculum View  
**Author:** Juan  
**Date:** Feb 2, 2026  
**Version:** v1.1  

## 0) 🧾 Changelog
### v1.0 → v1.1
- Added “🚀 Next best action” to reduce decision friction in the TODAY column
- Added lunch timer with end-of-break notifications (Notification API + toast fallback)
- Added missed assignment attention pattern (pulse + hourly reminders)
- Added small iconography for high-signal actions (e.g., submit/upload/watch)

## 1) 📌 Problem Statement
Pursuit’s student dashboard presents a week-based curriculum view that helps learners track daily activities, assessments, and deliverables. While functional and information-rich, students experience cognitive overload, weak visual hierarchy, and limited interaction clarity—especially during weeks with multiple assessments.

This can lead to:
- Missed submissions
- Confusion around priorities
If you're a student with high cognitive load and limited time, the dashboard should reduce decision friction and increase confidence.

## 2) 🎯 Goals & Success Metrics
### Goals
- Improve clarity of what matters today
- Reduce cognitive load when scanning the week
- Increase confidence that students are “on track”
- Make actions (submit, review, prepare) more obvious

### Success Metrics
- ↓ Missed or late submissions
- ↑ Daily engagement with dashboard
- ↓ Student questions about “what’s due”
- Positive qualitative feedback in retros

## 3) 👤 Target Users
- **Primary:** Pursuit student (career-switcher, high cognitive load, time-constrained)
- **Secondary:** Instructor/TA reviewing student progress

## 4) 🧠 Current UX/UI Issues (Observed)
1. **Cognitive Overload**
   - Too many similar-looking items
   - No strong separation between mandatory vs optional
2. **Weak Visual Hierarchy**
   - “TODAY” is highlighted, but priority inside Today is unclear
3. **Action Ambiguity**
   - CTAs (like “Submit link”) are easy to miss
4. **Progress Visibility**
   - No clear daily/weekly completion signals
5. **Limited Feedback Loops**
   - No clear “on track / behind” feedback

## 5) 🧩 Proposed Solution Overview
Introduce priority-driven structure, progress signaling, and action clarity without changing the curriculum content.

## 6) ✨ Key Features & Requirements

### 6.1 Priority Tagging System
Each activity has a visible tag:
- 🔴 **Required** (must complete)
- 🟡 **Recommended** (high value)
- ⚪ **Optional** (nice-to-have)

**Requirements**
- Tag visible at a glance
- Uses icon + label (not color alone)

### 6.2 “Today Focus” Panel
At the top of the selected day:
- **🎯 Today’s Focus** shows top 1–3 most important items

**Requirements**
- Only critical items appear here
- Reduces scanning effort

### 6.3 Progress Indicators
Add:
- Daily progress (e.g., `3 / 6`)
- Weekly progress (e.g., `12 / 20`)

**Requirements**
- Updates in real time
- Feels reassuring, not punitive

### 6.4 Stronger Primary CTAs
Replace subtle links with clear, consistent buttons:
- “⬆️ Submit Assessment”
- “📎 Upload PRD Draft”
- “▶️ Watch Required Video”

**Requirements**
- Action-oriented labels
- Consistent placement and styling

### 6.5 Expand / Collapse Task Details
Default view is a high-level list; clicking “Details” expands:
- Context
- Expectations
- Rubric links (future)

**Requirements**
- Reduces noise
- Preserves depth when needed

### 6.6 “Next Best Action” CTA (New in v1.1)
Add a “🚀 Next best action” button in Today Focus.

**Requirements**
- On click, automatically:
  - Finds the first incomplete 🔴 Required focus item (fallback to next incomplete focus item)
  - Scrolls to the task
  - Expands details
  - Briefly highlights the task
- If nothing is left, show an “All set” confirmation

### 6.7 Lunch Timer (New in v1.1)
Add a lunch break timer in the “Lunch” separator.

**Requirements**
- Start/Pause/Reset controls
- Visible countdown
- Notifies the student when time is up:
  - Prefer browser/system notification if allowed
  - Fallback to an in-page toast + sound

### 6.8 Missed Assignments Attention Pattern (New in v1.1)
Make missed assignments hard to overlook.

**Requirements**
- “Missed assignments” pill has a pulsing animation to grab attention
- Reminders roughly every hour (configurable)
  - Prefer Notification API if allowed
  - Fallback to in-page toast
- Respect reduced-motion preferences

## 7) 🚫 Out of Scope (This Version)
- Mobile-first redesign
- Calendar sync / external reminders integration
- Instructor analytics dashboard
- AI recommendations or personalization
- Authentication, server persistence, and real curriculum data fetching
- Full notification settings UI (snooze, quiet hours, custom cadence)

## 8) 🧪 Risks & Mitigations
- **Over-engineering:** keep default view simple; progressive disclosure
- **Student overwhelm:** focus panel + next best action reduces decision fatigue
- **Accessibility:** icon + label for tags; reduced-motion support

## 9) ✅ Implementation Notes (Current Prototype)
Implemented in:
- [index.html](index.html) (structure + JS behaviors)
- [styles.css](styles.css) (visual design + animations)

Behaviors included:
- Real-time daily/weekly progress updates
- Today Focus list generation
- Next best action scroll + expand + highlight
- Lunch timer + notifications/toast fallback
- Missed assignment pulsing + hourly reminder

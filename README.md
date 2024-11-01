## SCHEDULING 

## Overview 

- This project adds a scheduling feature to the Adobe Sidekick extension. It allows users to set dates for when content should be visible, so they can preview or publish it at specific times. This helps reduce manual steps and user errors when managing content.

## Existing Solutions 

- Adobe has an open pull request (PR #23) with similar features for scheduling in Sidekick. This PR adds date-based scheduling, but it’s still unmerged. We based this POC on that PR to see if it would work for us.

## What Was Implemented

- Date Input Field: Added a sidekick extension that by adding a date field scheduled content can be previewed (users can pick a date to see how content will look at that time).

## Content Display Rules:

- Each block (like columns or cards) has a row where the first cell is labeled “date”,
- The second cell has either:

    - A single date (to make the block visible after this date).

    - A date range (to show the block only within these dates).

- Sections use a similar setup. If there’s no date set, the section or block is always visible.

- Date Handling: Dates are saved in session storage so the page reloads with the new date setting. If there’s no date set content is shown by default.

## Code Highlights

- getTimestamp() and shouldBeDisplayed(): Decide if content should be shown based on current time and stored dates.

- scheduleBlocks() and scheduleSections(): Go through each block and section to check if they have a date and hide those not meant to be visible.

## Results

- This POC shows that date-based visibility works in Sidekick and can make previewing and publishing easier. It hides content not scheduled to be shown, reducing manual work.

## Limitations

- Security: Hidden content is still in the DOM, so it’s not secure for confidential data.
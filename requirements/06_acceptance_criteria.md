# Acceptance Criteria

## Epic 1: Stock Discovery and Ranking

### US1.1: Set Investment Priority

**AC1.1.1 – User Can Select Investment Priority**
- Given the user is on the main platform page
- When the user clicks on the investment priority selector
- Then a list of three options (ROI, Growth, Dividends) is displayed

**AC1.1.2 – User Can Confirm Priority Selection**
- Given the user has selected an investment priority
- When the user confirms their selection
- Then the platform acknowledges the selection and displays "Priority set to [selected metric]"

**AC1.1.3 – Only One Priority Can Be Active**
- Given the user has already selected a priority
- When the user selects a different priority
- Then the previous priority is deselected and the new priority becomes active

---

### US1.2: View Ranked Stock List

**AC1.2.1 – Top Stocks Are Ranked Correctly**
- Given the user has set an investment priority
- When the user requests to view the ranked list
- Then the top 10 stocks are displayed in descending order by the selected metric

**AC1.2.2 – Stock Information Is Displayed**
- Given a ranked stock list is displayed
- When the user views the list
- Then each stock displays company name, ticker symbol, and the value of the selected metric

**AC1.2.3 – Results Are Returned Within Time Limit**
- Given the user has set a priority and requested results
- When the ranking query is executed
- Then the top 10 stocks are displayed within 30 seconds

**AC1.2.4 – Stock List Responds to Priority Changes**
- Given the user has viewed a ranked list for one priority
- When the user changes their priority selection
- Then the stock list is updated within 30 seconds to reflect the new ranking

---

### US1.3: Access Stock Details

**AC1.3.1 – Additional Stock Details Are Available**
- Given a stock is displayed in the ranked list
- When the user clicks on the stock or a details button
- Then additional information is displayed (current price, sector, market cap)

**AC1.3.2 – Details Remain Accessible Without Navigation Loss**
- Given the user is viewing stock details
- When the user closes the details view
- Then the user returns to the ranked stock list without losing the original ranking

**AC1.3.3 – Details Are Accurate and Current**
- Given stock details are displayed
- When the user views the details
- Then the information is within 1% accuracy of the data source

---

### US1.4: Change Investment Criteria

**AC1.4.1 – User Can Switch Priorities Without Friction**
- Given the user is viewing a ranked list for one priority
- When the user selects a different priority
- Then the list updates and displays stocks ranked by the new priority within 30 seconds

**AC1.4.2 – Switching Criteria Does Not Require Re-entry**
- Given the user has changed their priority
- When the user switches back to a previous priority
- Then the platform immediately displays stocks ranked by the previous metric

---

## Epic 2: Fast and Simple User Experience

### US2.1: Quick Access to Results

**AC2.1.1 – Results Available Within Performance Target**
- Given the user has set their investment priority
- When the user requests to view results
- Then the top stock list is displayed within 2 minutes from initial platform access

**AC2.1.2 – Page Load Is Fast**
- Given the user navigates to the main platform
- When the page begins loading
- Then the page is fully loaded and interactive within 3 seconds

**AC2.1.3 – No Unnecessary Delays**
- Given the user has completed all input actions
- When awaiting the stock list
- Then loading indicators or progress feedback is visible to the user

---

### US2.2: Understand the Platform Immediately

**AC2.2.1 – Platform Is Intuitive Without Instructions**
- Given a new user opens the platform
- When the user surveys the interface
- Then all critical elements (priority selector, stock list, details) are clearly visible and understandable

**AC2.2.2 – Clear Labels and Naming**
- Given the user interacts with the platform
- When the user views buttons, fields, and sections
- Then all elements use clear, plain-language labels (e.g., "Investment Priority," "Top Stocks")

**AC2.2.3 – No Training Required to Perform Core Tasks**
- Given a first-time user
- When the user attempts to select a priority and view results
- Then the user can complete both actions without external help or documentation

---

### US2.3: Minimal Interaction Required

**AC2.3.1 – Setting Priority Requires Single Selection**
- Given the user is on the platform
- When the user wants to set their investment priority
- Then clicking the priority selector, selecting an option, and confirming represents no more than 3 interactions

**AC2.3.2 – Viewing Results Requires Minimal Clicks**
- Given the user has set their priority
- When the user wants to view results
- Then the action requires no more than 1 additional click

**AC2.3.3 – Changing Priorities Requires Minimal Interactions**
- Given the user is viewing results
- When the user wants to change their priority
- Then the action requires no more than 3 clicks total from the current state

---

## Epic 3: Data Accuracy and Trust

### US3.1: Verify Stock Metrics

**AC3.1.1 – Metrics Are Accurate**
- Given stock metrics are displayed
- When compared to the source data
- Then the displayed values are within 1% of the authoritative data source

**AC3.1.2 – Data Is Current**
- Given the user is viewing stock metrics
- When the user checks the data timestamp
- Then the data is no older than 7 days

**AC3.1.3 – Updates Are Reflected Promptly**
- Given stock metrics change in the source data
- When the weekly update cycle runs
- Then the platform reflects the updated metrics within 24 hours

---

### US3.2: Understand Metric Definitions

**AC3.2.1 – Definitions Are Accessible**
- Given the user is viewing the platform
- When the user hovers over or clicks a metric label
- Then a brief explanation of how the metric is calculated is displayed

**AC3.2.2 – Definitions Are Clear**
- Given a metric definition is displayed
- When the user reads the definition
- Then it explains the calculation in plain language without jargon

**AC3.2.3 – Definitions Are Consistent**
- Given a metric (e.g., ROI) is referenced in multiple places
- When the user views the definition in different locations
- Then the explanation is consistent and identical

---

## Epic 4: Continuous Access and Reliability

### US4.1: Access Platform Anytime

**AC4.1.1 – Platform Is Available During Business Hours**
- Given the user attempts to access the platform during 9 AM – 5 PM ET, Monday–Friday
- When the user navigates to the platform URL
- Then the platform is accessible and functional

**AC4.1.2 – Minimal Downtime**
- Given the platform is monitored for uptime
- When uptime statistics are measured during business hours
- Then the platform achieves 99% availability

---

### US4.2: Consistent Performance

**AC4.2.1 – Performance Under Load**
- Given multiple concurrent users are accessing the platform
- When at least 100 concurrent users are active
- Then response times remain ≤ 30 seconds for stock ranking queries

**AC4.2.2 – No User-Facing Degradation**
- Given the platform is operating under typical load
- When a user sets priority and requests results
- Then the user experiences consistent, responsive behavior without noticeable slowdowns

---

## Epic 5: Personalization and Preferences

### US5.1: Save Investment Preferences

**AC5.1.1 – Preferences Are Persisted**
- Given the user has set an investment priority
- When the user closes the browser or leaves the platform
- Then upon returning, the user's last selected priority is displayed

**AC5.1.2 – Saved Preference Is Accurate**
- Given the user has selected a preference
- When the user returns to the platform after several hours or days
- Then the saved preference matches the last selection made

**AC5.1.3 – User Can Reset Preferences**
- Given the user has saved preferences
- When the user clicks "Reset Preferences" or similar action
- Then the saved preference is cleared and the user must select a priority again

---

### US5.2: Compare Multiple Strategies

**AC5.2.1 – Quick Switching Between Priorities**
- Given the user is viewing results for one priority
- When the user selects a different priority
- Then the list updates within 30 seconds without page refresh

**AC5.2.2 – Previous Results Are Not Lost**
- Given the user has switched priorities multiple times
- When the user switches back to a previously viewed priority
- Then the stock rankings are immediately re-displayed (or updated within 30 seconds if data has changed)

**AC5.2.3 – User Can See Comparison Visually**
- Given the user has viewed results for multiple priorities
- When the user switches between priorities
- Then it is clear how stocks are ranked differently by the different metrics

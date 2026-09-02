# SWDC Calendar

An interactive website for viewing calendar data for Southwest Washington Dance Center (SWDC).  Automatically pulls data from a [google spreadsheet](https://docs.google.com/spreadsheets/d/1G4BoG5Jumb-N_HVgcvb5e1noY3rL4GG_F5kfpcgIl6s) which designated editors can modify.

## Screenshots
![Year Tab](screenshots/yearTab.png) 
![Month Tab](screenshots/monthTab.png) 
![Day Tab](screenshots/dayTab.png) 

## Spreadsheet Interface
Modifications to the spreadsheet will appear on the website after a refresh.  There are three tabs on the spreadsheet that may be edited.

### EventData
**Day-Level** entries contain a **Date**, **Title**, **Categories**, and **Notes**
- These entries populate the **month** and **year** tabs with titles and colors
- **Dates** must be in the format **mm/dd/yyyy**
  - you may also input a range of dates (two dates separated by a dash)
- **Title** may be any text
- **Categories** may be values from the "Categories" tab
  - the category determines the **color** on the month and year tabs
  - multiple categories may be applied to a given day (separated by commas), but only the first category determines the color
- **Notes** may be any text.  These are visible on the **day** tab.

**Event-Level** entries contain a **Description**, **Location**, **Start time**, **End time**, and **Instructors**.
- These entries populate the **day** tab on the **Day-Level** entry that preceded it
- These entries must leave column A blank, and start on column B
- **Description**, **Location**, and **Instructors** may be any text
- **Time** fields must be in a 12-hour time format (e.g. 4:15 PM or 12:30:59 AM)
- You can create a **Subtitle** by omitting all fields except **Description** (for additional notes, or for grouping of events)
- If only **Location** is omitted, the entry is applied to all locations (for things like breaks)

### WeeklyData
Contains schedules that repeat on a weekly basis. After specifying a time range, you can specify the schedule for each weekday within that time frame.
- Time ranges contain 3 cells: **Duration**, **Start date**, **End date**
  - **Duration** is the literal word "Duration"
  - **Start date** and **End date** are each in the format mm/dd/yyyy
- **Event-Level** entries are the same as for EventData, however the first entry in a group of entries must include a **day of the week** in column A, such as "Monday", which specifies which weekday the group applies to.

### CategoryData
Each entry consists of a **Category** and a **Color**.
- **Category** may be any text
- **Color** may be any CSS color
- "**No Class**" and "**Classes**" are special categories.  "Classes" corresponds to the WeeklyData, and "No Class" overrides "Classes".

### Notes / Restrictions
- Any empty lines will be ignored.
- Any line beginning with a # will be ignored.  This may be used to add comments.
- No cells may include double quotes or newlines since this breaks the parser currently.
- A change-log is saved automatically, so changes can be reverted if necessary.
- You may reference copies of the spreadsheet with a query parameter, e.g. `sheetid=19uhGgs5xKik_mL88TwFOr6L9ymopRCFCzgQ8Rk4OLPg`.  The copy must have the same **gids** for its tabs and have "anyone with the link can view" enabled.
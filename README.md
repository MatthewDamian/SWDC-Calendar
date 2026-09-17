# SWDC Calendar

An interactive website for viewing calendar data for Southwest Washington Dance Center (SWDC).  Automatically pulls data from a [google spreadsheet](https://docs.google.com/spreadsheets/d/1G4BoG5Jumb-N_HVgcvb5e1noY3rL4GG_F5kfpcgIl6s) which designated editors can modify.

## Screenshots
![Year Tab](screenshots/yearTab.png) 
![Month Tab](screenshots/monthTab.png) 
![Day Tab](screenshots/dayTab.png) 

## Spreadsheet Interface
You may **insert rows anywhere** and begin typing to make new entries.  After a couple of seconds, **refresh** the website to see the changes.  There are two tabs on the spreadsheet that may be edited: **EventData** and **Categories**.

### EventData
Rows on this tab may have one of two formats: **Day-Format** (Date String, Title, Categories, Notes), representing an entire day, or **Event-Format** (Filter, Description, Location, Start Time, End Time, Instructors), representing a single event within a day.

#### **Day-Format**
- Example: `9/7/2026` `Labor Day` `No Class`
- Inputting a **Date String** in column A makes that row a **Day Entry**
- Valid **Day Entries** are visible on the website as colored boxes
- **Date Strings** must be in the format **mm/dd/yyyy**
  - dates do not have to be in order
  - you may also input a range of dates (two dates separated by a dash)
  - Examples: `7/1/2026`, `8/17/2026-8/21/2026`
  - you may prefix a date string with **&** to signify an **additive entry** (explained below)
- **Title** (column B) may be any text
- **Categories** (column C) may be values from the "Categories" tab
  - these must be **spelled correctly**
  - the category determines the **color** on the website
  - multiple categories may be applied to a given day (separated by commas), but only the last category determines the color
- **Notes** (column D) may be any text.  These are visible on the **day** tab.
- By default, if two entries are applied to the same day, the latter overrides the former.  **Additive entries** add their schedule to the former instead.  Prepend the date string with the **&** symbol to make it an additive entry.
  - Examples: `&7/1/2026`, `&8/17/2026-8/21/2026`

#### **Event-Format**
- Example: ` `&nbsp;`Sugar Plum Pas` `Studio C` `7:00 pm` `8:30 pm` `Brianna`
- Rows that begin with a **blank** or a **day of the week** are in the **Event Format**
- These rows are applied to the **Day-Level** entry that preceded it
- You can add any number of **Event Format** rows below a **Day Format** row
- **Filter** (Column A) must be blank, or a day of the week, (e.g. "Monday")
  - restricts which weekdays the following event rows apply to
  - designed for schedules that repeat on a weekly basis
- **Description** (Column B) may be any text
- **Location** (Column C) may be any text
- **Start Time** (Column D) must be in a 12-hour time format, (e.g 4:15 PM)
- **End Time** (Column E) same as **Start Time**
- **Instructors** (Column F) may be any text
- **Special Entries**
  - You can create special entries by omitting certain fields
  - **Headers**
    - omit all fields except **Description**
    - used for additional notes, and to separate tables on the print page
  - **Everywhere Entry**
    - Only omit **Location**, the entry is applied to all locations
    - used for breaks or anything else that applies everywhere

### Categories
- Rows on this tab consist of a **Category** and a **Color**.
- **Category** (Column A) may be any text
- **Color** (Column B) may be any CSS color

### Notes
- Any empty rows will be ignored.
- Any row beginning with a **#** symbol will be ignored.
  This may be used to add comments.
- A change-log is saved automatically, so changes can be reverted if necessary.
- You can make a copy of the spreadsheet and share it (General Access: Anyone with the link).  Then you can view its data in the calendar website by adding `?sheetid=[copy sheet id here]` to the end of the main URL
- Here's a [practice site](https://matthewdamian.github.io/SWDC-Calendar/?sheetid=19uhGgs5xKik_mL88TwFOr6L9ymopRCFCzgQ8Rk4OLPg) with a [practice sheet](https://docs.google.com/spreadsheets/d/19uhGgs5xKik_mL88TwFOr6L9ymopRCFCzgQ8Rk4OLPg)
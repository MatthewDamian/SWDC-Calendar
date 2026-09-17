# SWDC Calendar

An interactive website for viewing calendar data for Southwest Washington Dance Center (SWDC).  Automatically obtains its data from a google spreadsheet.

![Year Tab](screenshots/yearTab.png) 
![Month Tab](screenshots/monthTab.png) 
![Day Tab](screenshots/dayTab.png) 

## Spreadsheet Interface
You may **insert rows anywhere** and begin typing to make new entries.  After waiting a couple of seconds, **refresh** the website to see the changes.  There are two tabs on the spreadsheet that may be edited: **EventData** and **Categories**.

### EventData
Rows on this tab may have one of two formats: **Day-Format**, representing an entire day, or **Event-Format**, representing a single event within a day.

#### **Day-Format** (Date String, Title, Categories, Notes)
- Example: `9/7/2026` `Labor Day` `No Class`
- Inputting a **Date String** in column A makes that row a **Day Entry**
- Valid **Day Entries** are visible on the website
- **Date Strings** must be in the format **mm/dd/yyyy**
  - dates do not have to be in order
  - you may also input a range of dates (two dates separated by a dash) e.g. `8/17/2026-8/21/2026`
  - If two entries are applied to the same day, the latter overrides the former.  You may prepend the latter date string with the **&** symbol to make it **add** its data to the former instead.  Example: `& 8/17/2026-8/21/2026`
- **Title** (column B) may be any text
- **Categories** (column C) may be names from the "Categories" tab
  - these must be **spelled correctly**
  - the category determines the **color** on the website
  - multiple categories may be applied to a given day (separated by commas), but only the last category determines the color
- **Notes** (column D) may be any text.  These are visible on the **day tab** of the website.

#### **Event-Format** (Filter, Description, Location, Start Time, End Time, Instructors)
- Example: ` `&nbsp;`Sugar Plum Pas` `Studio C` `7:00 pm` `8:30 pm` `Brianna`
- Rows that begin with a **blank** or a **day of the week** become **Event Entries**
- These entries are applied to the **Day Entry** that preceded it
- Valid **Event Entries** are visible on the **day tab** of the website
- You can add any number of **Event Entries** below a **Day Entry**
- **Filter** (Column A) must be blank, or a day of the week, (e.g. "Monday")
  - non blank filters restrict which weekdays the following event rows apply to
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
    - omit only **Location**
    - the entry is applied to all locations
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
- Here's a [practice site](https://matthewdamian.github.io/SWDC-Calendar/?sheetid=19uhGgs5xKik_mL88TwFOr6L9ymopRCFCzgQ8Rk4OLPg) with a [practice sheet](https://docs.google.com/spreadsheets/d/19uhGgs5xKik_mL88TwFOr6L9ymopRCFCzgQ8Rk4OLPg).  Feel free to make changes to the sheet to observe the effect on the practice site.

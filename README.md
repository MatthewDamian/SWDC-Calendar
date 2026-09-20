# SWDC Calendar

An interactive website for viewing calendar data for Southwest Washington Dance Center (SWDC).  Automatically obtains its data from a google spreadsheet.

<table>
  <tr>
    <td valign="middle">
      <img src="screenshots/yeartab.png">
    </td>
    <td valign="middle">
      <img src="screenshots/monthtab.png">
    </td>
  </tr>
  <tr>
    <td valign="middle">
      <img src="screenshots/daytab.png">
    </td>
    <td valign="middle">
      <img src="screenshots/walkthrough/print2.png">
    </td>
  </tr>
</table>

### Table of Contents
* [Walkthrough](#walkthrough)
  * [Adding Events](#adding-events)
  * [Special Features](#special-features)
* [Specification](#specification)
  * [Date Format](#date-format)
  * [Schedule Format](#schedule-format)
  * [Categories](#categories)
* [Notes](#notes)


## Walkthrough
Click on "View Google Sheet" from the website to begin editing the site's data (provided you have editor access).  You may **insert rows anywhere** and begin typing to make new entries.  After a second, **refresh** the website to see the changes.  

### Adding Events
With a blank spreadsheet, here's what you'd see on the year tab:  
<table>
  <tr>
    <td valign="middle">
      <img src="screenshots/walkthrough/sheets1.png">
    </td>
    <td valign="middle">
      <img src="screenshots/walkthrough/site1.png">
    <td>
  </tr>
</table>

After adding some categories:
<table>
  <tr>
    <td valign="middle">
      <img src="screenshots/walkthrough/sheets2.png">
    </td>
    <td valign="middle">
      <img src="screenshots/walkthrough/site2.png">
    <td>
  </tr>
</table>

After adding some events (switch to the **Events Tab** at the bottom of the spreadsheet):

<table>
  <tr>
    <td valign="middle">
      <img src="screenshots/walkthrough/sheets3.png">
    </td>
    <td valign="middle">
      <img src="screenshots/walkthrough/site3.png">
    <td>
  </tr>
</table>

And here's the Month and Day tabs of the barbecue event:
<table>
  <tr>
    <td valign="middle">
      <img src="screenshots/walkthrough/site4.png">
    </td>
    <td valign="middle">
      <img src="screenshots/walkthrough/site5.png">
    <td>
  </tr>
</table>

Here's the Day tab after adding a schedule:
<table>
  <tr>
    <td valign="middle">
      <img src="screenshots/walkthrough/sheets4.png">
    </td>
    <td valign="middle">
      <img src="screenshots/walkthrough/site6.png">
    <td>
  </tr>
</table>

Note that the schedule entries are applied to the date entry that preceded it, and follow a different format.  The date entry follows the format **[Date(s), Title, Categories, Notes]**, but the schedule entries follow the format **[(Weekday), Description, Location, Start Time, End Time, Instructors]**.

### Special Features

You can also add sections/notes within the schedule entries, by adding entries with only a **Description**.

<table>
  <tr>
    <td valign="middle">
      <img src="screenshots/walkthrough/sheets5.png">
    </td>
    <td valign="middle">
      <img src="screenshots/walkthrough/site7.png">
    <td>
  </tr>
</table>

And here's the corresponding print page:
<table>
  <tr>
    <td valign="middle">
      <img src="screenshots/walkthrough/print1.png" width="50%">
    </td>
  </tr>
</table>

For date entries that span multiple days, adding a schedule to it applies that schedule to **every** day within that range.  You can section those schedules by adding a **Weekday** in the first column.

<table>
  <tr>
    <td valign="middle">
      <img src="screenshots/walkthrough/sheets6.png">
    </td>
    <td valign="middle">
      <img src="screenshots/walkthrough/site8.png">
    <td>
  </tr>
  <tr>
    <td valign="middle">
      <img src="screenshots/walkthrough/site9.png">
    </td>
    <td valign="middle">
      <img src="screenshots/walkthrough/site10.png">
    <td>
  </tr>
</table>

Note that for large date ranges that span multiple weeks, those sections would repeat weekly.  This can be used for anything that repeats on a weekly basis.

If two date entries are applied to the exact same date, the latter one overwrites the former which is useful for holidays.  Overwriting can be prevented by prepending the latter entry with the **&** symbol, which makes it only replace the title and color, while adding its category, notes, and schedule to the former.

## Specification

Rows on the **Events Tab** may have one of two formats: **Date-Format**, representing a date or range of dates, or **Schedule-Format**, representing a single event within a day.

### Date-Format
|Date|Title|Categories|Notes|
|-|-|-|-|
|9/7/2026|Labor&nbsp;Day|No&nbsp;Class| |
- Inputting a **Date String** in column A makes that row a **Date Entry**
- **Date Strings** must be in the format **mm/dd/yyyy**
  - dates do not have to be in order
  - you may also input a range of dates (two dates separated by a dash) e.g. `8/17/2026-8/21/2026`
  - If two entries are applied to the same day, the latter overrides the former.  You may prepend the latter date string with the **&** symbol to make it **add** its data to the former instead.  Example: `& 8/17/2026-8/21/2026`
- **Title** (column B) may be any text
- **Categories** (column C) must be names from the "Categories" tab
  - these must be **spelled correctly**
  - the category determines the **color** on the website
  - multiple categories may be applied to a given day (separated by commas)
- **Notes** (column D) may be any text.  These are visible on the **day tab** of the website.

### Schedule-Format
|(Weekday)|Description|Location|Start&nbsp;Time|End&nbsp;Time|Instructors|
|-|-|-|-|-|-|
| |Sugar Plum Pas|Studio C|7:00&nbsp;pm|8:30&nbsp;pm|Brianna|
- Rows that begin with a **blank** or a **weekday** become **Schedule Entries**
- These entries are applied to the **Date Entry** that preceded it
- Valid **Schedule Entries** are visible on the **day tab** of the website
- You can add any number of **Schedule Entries** below a **Date Entry**
- **Weekday** (Column A, optional)
  - event entries beneath a **date range** are applied to every day within that range, unless you add a **weekday** (like "Monday") in column A, restricting which weekdays those entries are applied to
  - a weekday applies to every entry below and including it, until the next weekday or date entry
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
Rows on the **Categories Tab** must have a category and a color.

|Category|Color|
|-|-|
|Performances|Pink|
- **Category** (Column A) may be any text
- **Color** (Column B) may be any [CSS color](https://davidbau.com/colors/)

### Notes
- Any empty rows will be ignored.
- Any row beginning with a **#** symbol will be ignored.
  This may be used to add comments.
- A change-log is saved automatically, so changes can be reverted if necessary.
- Here's a [practice site](https://matthewdamian.github.io/SWDC-Calendar/?sheetid=19uhGgs5xKik_mL88TwFOr6L9ymopRCFCzgQ8Rk4OLPg) with a [practice sheet](https://docs.google.com/spreadsheets/d/19uhGgs5xKik_mL88TwFOr6L9ymopRCFCzgQ8Rk4OLPg).  Feel free to make changes to the sheet to observe the effect on the practice site.

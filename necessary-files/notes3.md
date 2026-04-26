Parameterized Reports:
- Course-wise Routine (Page 15)

<h2>Page 15 — Course-wise Routine</h2>
Step 1: Create Page
Go to App Builder → Create Page<br>
Choose: Report → Interactive Report<br>
Page Number: 15<br>
Page Name: Course-wise Routine <br>
SQL Query:
```sql
SELECT 
    c.course_code AS "Course Code",
    c.course_title AS "Course Title",
    c.credits AS "Credits",
    s.section_no AS "Section No",
    s.section_type AS "Type",
    f.full_name AS "Faculty Name",
    f.initials AS "Initials",
    t.start_time  AS "Start Time",
    t.end_time AS "End Time",
    t.day_combo AS "Days",
    r.room_name AS "Room"
FROM SECTION s
JOIN COURSE c  ON s.course_id = c.course_id
JOIN FACULTY f ON s.faculty_id = f.faculty_id
JOIN TIME_SLOT t ON s.slot_id = t.slot_id
JOIN ROOM r ON s.room_id = r.room_id
WHERE c.course_code = :P8_COURSE
ORDER BY s.section_no, s.section_type
<h2>Create Input Parameter (Dropdown)</h2>
In Page Designer:<br>
Right-click Body → Create Page Item<br>
Set:<br>
Name: P15_COURSE<br>
Type: Select List<br>
Label: Select Course<br>

- Right-click on Body in the left panel
- Click Create Page Item
- Fill in:Name:    P15_COURSE
- Type:    Select List
- Label:   Select Faculty

- LOV:
SELECT course_code || ' - ' || course_title AS display,
       course_code AS return
FROM   COURSE
ORDER BY course_code
- Display Null Value: ON
- Null Display Value: - Select Course -
<h2>Connect Dropdown to Report</h2>
- Click Faculty-wise Routine (region)
- In right panel → find:
- Page Items to Submit
- Add:P15_COURSE 
- RUN

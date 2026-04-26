Parameterized Reports:
- Faculty-wise Routine (Page 14)

<h2>Page 14 — Faculty-wise Routine</h2>
Step 1: Create Page
Go to App Builder → Create Page<br>
Choose: Report → Interactive Report<br>
Page Number: 14<br>
Page Name: Faculty-wise Routine <br>
SQL Query:
SELECT 
    f.full_name AS "Faculty Name",
    f.initials  AS "Initials",
    c.course_code AS "Course Code",
    c.course_title  AS "Course Title",
    c.credits AS "Credits",
    s.section_no AS "Section No",
    s.section_type AS "Type",
    t.start_time AS "Start Time",
    t.end_time AS "End Time",
    t.day_combo AS "Days",
    r.room_name  AS "Room"
FROM SECTION s
JOIN FACULTY f ON s.faculty_id = f.faculty_id
JOIN COURSE c  ON s.course_id = c.course_id
JOIN TIME_SLOT t ON s.slot_id = t.slot_id
JOIN ROOM r ON s.room_id = r.room_id
WHERE f.initials = :P7_FACULTY
ORDER BY c.course_code, s.section_type, s.section_no
<h2>Create Input Parameter (Dropdown)</h2>
In Page Designer:<br>
Right-click Body → Create Page Item<br>
Set:<br>
Name: P14_FACULTY<br>
Type: Select List<br>
Label: Select Faculty<br>

- Right-click on Body in the left panel
- Click Create Page Item
- Fill in:Name:    P14_FACULTY
- Type:    Select List
- Label:   Select Faculty

- LOV:
SELECT full_name || ' (' || initials || ')' AS display,
       initials AS return
FROM   FACULTY
ORDER BY full_name
- Display Null Value: ON
- Null Display Value: - Select Faculty -
<h2>Connect Dropdown to Report</h2>
- Click Faculty-wise Routine (region)
- In right panel → find:
- Page Items to Submit
- Add:P14_FACULTY 
- RUN

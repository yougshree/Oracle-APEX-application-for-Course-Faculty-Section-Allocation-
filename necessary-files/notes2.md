Parameterized Reports:
- Faculty-wise Routine (Page 14)
- Course-wise Routine (Page 8)
- Room-wise Routine (Page 9)
<h2>Page 14 — Faculty-wise Routine</h2>
Step 1: Create Page
Go to App Builder → Create Page<br>
Choose: Report → Interactive Report<br>
Page Number: 14<br>
Page Name: Faculty-wise Routine <br>
SQL Query:
SELECT <br>
    f.full_name AS "Faculty Name",<br>
    f.initials  AS "Initials",<br>
    c.course_code AS "Course Code",<br>
    c.course_title AS "Course Title",<br>
    c.credits  AS "Credits",<br>
    s.section_no AS "Section No",<br>
    t.start_time AS "Start Time",<br>
    t.end_time AS "End Time",<br>
    t.day_combo  AS "Days",<br>
    r.room_name AS "Room"<br>
FROM SECTION s<br>
JOIN FACULTY f ON s.faculty_id = f.faculty_id<br>
JOIN COURSE c ON s.course_id  = c.course_id<br>
JOIN TIME_SLOT t ON s.slot_id   = t.slot_id<br>
JOIN ROOM r ON s.room_id    = r.room_id<br>
WHERE f.initials = :P14_FACULTY<br>
ORDER BY c.course_code, s.section_no<br>
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

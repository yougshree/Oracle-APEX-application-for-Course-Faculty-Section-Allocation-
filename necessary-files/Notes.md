a) Creating the APEX Application: 
APEX home screen-> New Application-> fill  application details: Name:EWU Course Allocation System.
Create Application->Run Application

b)Create Report + Form pages:
- Page 2:Faculty->  Report type: Interactive Report->  Page name: Faculty Management ->Table: FACULTY -> Create.
- Page 3:Course->  Report type:Interactive Report->  Page name: Course Management ->Table: COURSE -> Create.
- Page 4:Room->  Report type:Interactive Report->  Page name: Room Management ->Table: ROOM -> Create.
- Page 5:Time Slot->  Report type:Interactive Report->  Page name: Time Slot Management ->Table: TIME_SLOT -> Create.

c)Create the Master-Detail page
- Create Page->Choose Master Detail->Stacked.
- Master table settings: Table:COURSE, Page name: Section Allocation.
- Detail table settings: Table: SECTION.
- Primary Key Column 1: SECTION_ID (Number), Primary Key Column 2: COURSE_ID -> COURSE_ID [The left COURSE_ID is from the SECTION table — it's the foreign key. The right COURSE_ID is from the COURSE table — it's the primary key].

d) LOV dropdowns:
- Open the master detail page.

 
- click->section->faculty_id->
- right side panel->Number Field. ->Change Type to: Select List.->Header name: Faculty -> List of Values: SQL Query.
SQL in the query box
SELECT full_name || ' (' || initials || ')' AS display,
       faculty_id AS return
FROM   FACULTY
ORDER BY full_name
- Display Extra Values: ON
- Null Display Value:   - Select Faculty -

- same for slot_id, ->Header name: Time Slot
- SQL:
- SELECT start_time || ' - ' || end_time || ' (' || day_combo || ')' AS display,
       slot_id AS return
FROM   TIME_SLOT
ORDER BY start_time, day_combo
- Display Null Value:   ON
- Null Display Value:   - Select Time Slot -

- same for room_id->Header name: Room
SQL:
SELECT room_name || ' (' || room_type || ')' AS display,
       room_id AS return
FROM   ROOM
ORDER BY room_type, room_name
- Display Null Value:   ON
- Null Display Value:   - Select Room -
- Save
- Run Page


) If someone want to change admin username and password:
BEGIN
  APEX_UTIL.CREATE_USER(
    p_user_name    => 'ADMIN',
    p_web_password => 'Admin1234!'
  );
  COMMIT;
END;
/

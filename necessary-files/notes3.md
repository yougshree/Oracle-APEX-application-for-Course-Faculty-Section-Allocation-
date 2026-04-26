# Page 16 — Room-wise Routine (Simple Notes)
---

## 1 — Create Page
App Builder → Create Page → Report → Interactive Report

* Page Number: 16
* Page Name: Room-wise Routine

SQL:
```sql 
SELECT 
    r.room_name        AS "Room",
    r.room_type        AS "Room Type",
    c.course_code      AS "Course Code",
    c.course_title     AS "Course Title",
    s.section_no       AS "Section No",
    s.section_type     AS "Type",
    s.semester         AS "Semester"
FROM SECTION s
JOIN COURSE c ON s.course_id = c.course_id
JOIN ROOM r   ON s.room_id   = r.room_id
WHERE r.room_name = :P16_ROOM
ORDER BY s.section_no;
```
Click **Next → Create Page**

---

## 2 — Add Dropdown

After page is created:

* Go to Page Designer
* Right-click **Body** → Create Page Item

Set:

* Name: `P16_ROOM`
* Type: Select List
* Label: Select Room
* Page Action on Selection: Submit Page

---

## 3 — Dropdown Data (LOV)

Type: SQL Query

```sql 
SELECT 
    room_name || ' (' || room_type || ')' AS display,
    room_name AS return
FROM ROOM
ORDER BY room_type, room_name;
```

---

## 4 — Default Option

* Display Null Value: ON
* Null Display Value: `- Select Room -`

---

## 5 — Connect Dropdown to Report

* Click the report region
* Find **Page Items to Submit**
* Add: `P16_ROOM`

---

## 6 — Run

Click **Save → Run Page**

---

## Final Result

* You select a room
* Page reloads
* Report shows all classes in that room

---

## Quick Checks (if not working)

* Did you add `P16_ROOM` in Page Items to Submit?
* Is `room_name` matching correctly?
* Is there data in SECTION table?

---

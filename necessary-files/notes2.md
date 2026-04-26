# Page 15 — Course-wise Routine (Simple Notes)

## Create Page
App Builder → Create Page → Report → Interactive Report

* Page Number: 15
* Page Name: Course-wise Routine

SQL:

```sql
SELECT 
    c.course_code AS "Course Code",
    c.course_title AS "Course Title",
    c.credits  AS "Credits",
    s.section_no AS "Section No",
    s.section_type  AS "Type",
    s.semester  AS "Semester"
FROM SECTION s
JOIN COURSE c  ON s.course_id  = c.course_id
LEFT JOIN FACULTY f ON s.faculty_id = f.faculty_id
LEFT JOIN TIME_SLOT t ON s.slot_id  = t.slot_id
LEFT JOIN ROOM r  ON s.room_id = r.room_id
WHERE c.course_code = :P15_COURSE
ORDER BY s.section_no;
```
Click **Next → Create Page**

---

## 2 — Add Dropdown

After page is created:

* Go to Page Designer
* Right-click **Body** → Create Page Item

Set:

* Name: `P15_COURSE`
* Type: Select List
* Label: Select Course
* Page Action on Selection: Submit Page

---

## 3 — Dropdown Data (LOV)

Type: SQL Query

```sql
SELECT 
    course_code || ' - ' || course_title AS display,
    course_code AS return
FROM COURSE
ORDER BY course_code;
```

---

## 4 — Add Default Option

* Display Null Value: ON
* Null Display Value: `- Select Course -`

---

## 5 — Connect Dropdown to Report

* Click report region
* Find **Page Items to Submit**
* Add: `P15_COURSE`

---

## 6 — Run

Click **Save → Run Page**

---

## Final Result

* You select a course
* Page reloads
* Report shows only that course’s sections

---

## Quick Checks (if not working)

* Did you add `P15_COURSE` in Page Items to Submit?
* Is course_code correct in table?
* Is there data in SECTION table?

---

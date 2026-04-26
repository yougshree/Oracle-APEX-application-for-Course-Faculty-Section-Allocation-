# Page 14 — Faculty-wise Routine (Oracle APEX)

## Objective

Create an **Interactive Report** that displays the routine for a selected faculty member.

---

## 1 — Create the Report Page

Navigate to:

**App Builder → Create Page → Report → Interactive Report**

Fill in the following details:

* **Page Number:** 14
* **Page Name:** Faculty-wise Routine

### SQL Query:

```sql
SELECT 
    f.full_name  AS "Faculty Name",
    c.course_code AS "Course Code",
    s.section_no  AS "Section No",
    s.section_type AS "Type",
    s.semester  AS "Semester"
FROM SECTION s
JOIN COURSE c  ON s.course_id  = c.course_id
JOIN FACULTY f ON s.faculty_id = f.faculty_id
WHERE f.initials = :P14_FACULTY
ORDER BY c.course_code;
```

Click **Create Page**.

---

## 2 — Add Faculty Selection (Dropdown)

After the page is created:

* Go to **Page Designer**
* In the left panel → Right-click **Body** → **Create Page Item**

### Configure the item:

* **Name:** `P14_FACULTY`
* **Type:** Select List
* **Label:** Select Faculty
* **Page Action on Selection:** Submit Page

---

## 3 — Add List of Values (LOV)

Set:

* **Type:** SQL Query

### SQL:

```sql
SELECT full_name || ' (' || initials || ')' AS display,
       initials AS return
FROM FACULTY
ORDER BY full_name;
```

---

## 4 — Null Option

* **Display Null Value:** ON
* **Null Display Value:** `- Select Faculty -`

---

## 5 — Submit Item to Report

* Click on the **Report Region**
* In the right panel, find:

  * **Page Items to Submit**
* Add:

  ```
  P14_FACULTY
  ```

---

## 6 — Save & Run

Click **Save**, then **Run Page**.

---

## Result

Dynamic **Faculty-wise Routine Report** where:

* User selects a faculty from the dropdown
* Page reloads automatically
* Report filters data based on selected faculty

---

## Notes

* Ensure `initials` in FACULTY table are unique
* If no data appears, verify:

  * `SECTION.faculty_id` mapping
  * Correct initials selection
* This same logic can be reused for:

  * Course-wise Routine
  * Room-wise Routine

---

## 🚀 Status

✔ Interactive filtering implemented
✔ Clean UI with dropdown
✔ Fully dynamic report

---

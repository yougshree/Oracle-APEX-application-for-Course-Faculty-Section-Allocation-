a) Creating the APEX Application: 
APEX home screen-> New Application-> fill  application details: Name:EWU Course Allocation System.
Create Application->Run Application

b)Create Report + Form pages:
Page 2:Faculty->  Report type: Interactive Report->  Page name: Faculty Management ->Table: FACULTY -> Create.
Page 3:Course->  Report type:Interactive Report->  Page name: Course Management ->Table: COURSE -> Create
Page 4:Room->  Report type:Interactive Report->  Page name: Room Management ->Table: ROOM -> Create
Page 5:Time Slot->  Report type:Interactive Report->  Page name: Time Slot Management ->Table: TIME_SLOT -> Create

c)Create the Master-Detail page
Create Page->Choose Master Detail->Stacked.
Master table settings: Table:COURSE, Page name: Section Allocation.
Detail table settings: Table: SECTION.
Primary Key Column 1: SECTION_ID (Number), Primary Key Column 2: COURSE_ID -> COURSE_ID [The left COURSE_ID is from the SECTION table — it's the foreign key
The right COURSE_ID is from the COURSE table — it's the primary key]

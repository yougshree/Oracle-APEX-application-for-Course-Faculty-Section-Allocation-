--drop
ALTER TABLE SECTION DROP COLUMN section_type;
-add because class and theory time and credit is diffrent and faculty may vary:
ALTER TABLE SECTION 
ADD section_type VARCHAR2(10) DEFAULT 'Theory' 
CHECK (section_type IN ('Theory','Lab'));

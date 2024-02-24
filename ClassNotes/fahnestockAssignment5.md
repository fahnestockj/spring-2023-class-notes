

# Fahnestock Assignment 5
7/6/2022
Professor Rawlins
ELEC 3225-01


### Group Members:
* Thomas Rice - Created the menu, log/log out, search all courses, and add/remove courses from system

* Jacob Fahnestock - Created the add/remove courses from semester schedule, assemble and print course roster for Instructor, and search courses based on parameters

### [Repository Link](https://github.com/ricet3ATWIT/LeopardWeb5/tree/main)

## Figure 1.1 Student Add Course to Semester Schedule
```python
def addCourseToSemesterSchedule(self, cursor):
	"""Allows admins to add a course to the 'SEMESTERSCHEDULE' table. Created by Jacob."""
	if input("Add courses to semester schedule. Hit enter to continue, or type 'exit' to go back: ") == 'exit' : return
	crn = input('CRN: ')
	cursor.execute("SELECT * FROM COURSE WHERE CRN = '%s';" % (crn))
	course = cursor.fetchone()
	if course == None:
		print("Course not found") 
	else:
		try:
			cursor.execute("""INSERT INTO SEMESTERSCHEDULE VALUES('%s', '%s', '%s');""" % (crn, self.getID(), course[8]))
		except:
			print('Course already in semester schedule')

```

## Figure 1.2 Terminal Output
![[Pasted image 20220706171349.png]]

## Figure 1.3 Class Schedule in Database 
![[Pasted image 20220706172153.png]]

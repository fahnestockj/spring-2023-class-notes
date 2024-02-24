# Assignment 1
Jacob Fahnestock
5/23/2022 
Professor Rawlins
ELEC3225

## Waterfall Model
The waterfall model is a Gantt Chart:
![[Pasted image 20220523082042.png]]

#### Requirements Analysis
Here is a list of the requirements for scheduling system. 
-  Database of users: the system should work for 100 students, 10 instructors, and 1 admin, however, we will test with fewer. 
- Database of courses: this will contain information such as the CRN, course name, times, and instructor. 
 *  Three types of users:
	 *  Student – can register, can see available courses and their own schedule. 
	 *  Instructor – can see available courses and their own course roster.
	 *  Admin – can see everything, can edit courses/users/schedules. 

• The system should include multiple semesters, print-out of schedule, scheduling preferences. 
• The system as a whole and all components must be tested thoroughly


### System Software and Design
This assigment will use OOP to abstract each user type as a custom object with methods relevant to that user. The main abstraction will be the use of the [Django](https://www.djangoproject.com/) web framework. Django 

# Fahnestock Assignment 3
6/14/2022
Professor Rawlins
ELEC 3225-01
#### Figure 1:  Query for Instructor(s) by Course
```python
courseName = input("Course Name: ")
cursor.execute("""SELECT * FROM COURSE WHERE TITLE = '%s' """ % (courseName))
query_result = cursor.fetchall()
if(len(query_result) == 0):
  print("Course not found")
else:
  department = query_result[0][2]
  cursor.execute("""SELECT * FROM INSTRUCTOR WHERE DEPT = '%s' """ % (department))
  query_result = cursor.fetchall()
  if(len(query_result) == 0):
    print("No instructor found")
  else:
    print("Instructor(s) found: ")
    for row in query_result:
      print(row)
```


#### Figure 2: Database Course Table
![[Pasted image 20220614204954.png]]
#### Figure 3: Database Admin Table
![[Pasted image 20220614205013.png]]
#### Figure 4: Program Output
![[Pasted image 20220614205100.png]]
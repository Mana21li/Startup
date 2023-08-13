# Startup


```
 if (!registeredCourses.containsKey(studentId)) {
            registeredCourses.put(studentId, courseIds);
            System.out.println("New user registered to course(s) successfully.");
            
            // Print course names
            System.out.println("Registered courses for user " + studentId + ":");
            for (Integer courseId : courseIds) {
                String courseName = Courses.get(courseId);
                if (courseName != null) {
                    System.out.println(courseName);
                }
            }
            
            return true;
        }
        return false;
```

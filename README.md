# Startup


 
 if (!registeredCourses.containsKey(studentId)) {
            registeredCourses.put(studentId, courseIds);
            System.out.println("New user registered to course(s) successfully.");
            return true;
        }
        return false;

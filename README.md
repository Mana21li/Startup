# Startup


 Map<Integer, String> Courses = Map.of(
        101, "Maths",
        102, "Physics",
        103, "Chemistry",
        104, "English",
        105, "Hindi",
        109, "Sanskrit",
        201, "History"
    );

    // ... rest of your code ...

    @Override
    public boolean registerCourse(Long StudentId, List<Integer> CourseIds) {
        List<Integer> regCourses = registeredCourses.get(StudentId);
        if (regCourses != null) {
            boolean allCoursesValid = true;
            for (Integer courseId : CourseIds) {
                if (!Courses.containsKey(courseId)) {
                    allCoursesValid = false;
                    break;
                }
            }
            if (allCoursesValid) {
                regCourses.addAll(CourseIds);
                System.out.println("Registration Successful");
                return true;
            } else {
                System.out.println("Invalid course(s) specified.");
                return false;
            }
        }
        return false;
    }

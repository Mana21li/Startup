# Startup


import java.util.List;
import java.util.Map;
import java.util.HashMap;

public class StudentDAOImpl implements StudentDAO {
    // Database simulation
    Map<Long, String> credential = Map.of(1001L, "user1", 1002L, "user2");

    Map<Long, List<Integer>> registeredCourses = Map.of(
        1001L, List.of(101, 102, 103, 104),
        1002L, List.of(103, 104, 201)
    );

    Map<Long, Map<Integer, List<String>>> gradeCard = Map.of(
        1001L, Map.of(
            1, List.of("Maths: A", "Physics: B", "Chemistry: A")
        ),
        1002L, Map.of(
            1, List.of("Maths: B", "Physics: B", "Chemistry: C")
        )
    );

    public void credentialCheck(Long studentId, String password) {
        String storedPassword = credential.get(studentId);
        if (storedPassword != null && storedPassword.equals(password)) {
            System.out.println("Credentials are valid.");
        } else {
            System.out.println("Invalid credentials.");
        }
    }

    public boolean registerCourse(Long studentId, List<Integer> courseIds) {
        List<Integer> existingCourses = registeredCourses.get(studentId);
        if (existingCourses != null) {
            existingCourses.addAll(courseIds);
            System.out.println("Courses registered successfully.");
            return true;
        }
        return false;
    }

    public void getGrade(int studentId) {
        Map<Integer, List<String>> studentGrades = gradeCard.get((long) studentId);
        if (studentGrades != null) {
            System.out.println("Grades for student " + studentId + ":");
            for (Map.Entry<Integer, List<String>> entry : studentGrades.entrySet()) {
                int semester = entry.getKey();
                List<String> grades = entry.getValue();
                System.out.println("Semester " + semester + " grades: " + grades);
            }
        } else {
            System.out.println("Student not found.");
        }
    }

    public boolean addCourse(int courseId, int studentId) {
        List<Integer> existingCourses = registeredCourses.get((long) studentId);
        if (existingCourses != null && !existingCourses.contains(courseId)) {
            existingCourses.add(courseId);
            System.out.println("Course added successfully.");
            return true;
        }
        return false;
    }

    public boolean dropCourse(int courseId, int studentId) {
        List<Integer> existingCourses = registeredCourses.get((long) studentId);
        if (existingCourses != null && existingCourses.contains(courseId)) {
            existingCourses.remove(Integer.valueOf(courseId));
            System.out.println("Course dropped successfully.");
            return true;
        }
        return false;
    }

    public void viewRegisteredCourses(int studentId) {
        List<Integer> courses = registeredCourses.get((long) studentId);
        if (courses != null) {
            System.out.println("Registered courses for student " + studentId + ": " + courses);
        } else {
            System.out.println("Student not found.");
        }
    }
}

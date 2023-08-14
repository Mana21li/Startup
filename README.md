# Startup

import java.sql.Connection;
import java.sql.PreparedStatement;
import java.sql.ResultSet;
import java.sql.SQLException;

public class CourseManager {

    // ... Your other methods and database connection code ...

    public void viewRegisteredCourses(Long studentId, String courseIdList) {
        String[] courseIds = courseIdList.split(",");

        String query = "SELECT courseName FROM courses WHERE courseId IN (";
        for (int i = 0; i < courseIds.length; i++) {
            query += "?";
            if (i < courseIds.length - 1) {
                query += ",";
            }
        }
        query += ")";

        try (Connection connection = getConnection();
             PreparedStatement preparedStatement = connection.prepareStatement(query)) {

            for (int i = 0; i < courseIds.length; i++) {
                preparedStatement.setString(i + 1, courseIds[i]);
            }

            ResultSet resultSet = preparedStatement.executeQuery();
            while (resultSet.next()) {
                String courseName = resultSet.getString("courseName");
                System.out.println("Course Name: " + courseName);
            }
        } catch (SQLException e) {
            e.printStackTrace();
        }
    }
}

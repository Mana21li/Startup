# Startup


import java.sql.Connection;
import java.sql.PreparedStatement;
import java.sql.ResultSet;
import java.sql.SQLException;
import java.util.HashMap;
import java.util.Map;

public class StudentDAOImpl implements StudentDAO {

    // ... (previous code)

    @Override
    public Map<Integer, String> getGrades(Long studentId) {
        Map<Integer, String> gradesMap = new HashMap<>();
        try {
            String selectQuery = "SELECT course_id, grade FROM report_card WHERE student_id = ?";
            PreparedStatement preparedStatement = conn.prepareStatement(selectQuery);
            
            // Set parameter
            preparedStatement.setLong(1, studentId);
            
            ResultSet resultSet = preparedStatement.executeQuery();
            
            while (resultSet.next()) {
                int courseId = resultSet.getInt("course_id");
                String grade = resultSet.getString("grade");
                gradesMap.put(courseId, grade);
            }
            
            resultSet.close();
            preparedStatement.close();
        } catch (SQLException e) {
            e.printStackTrace();
        }
        return gradesMap;
    }

    // ... (remaining methods)
}

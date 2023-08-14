# Startup
import java.sql.Connection;
import java.util.HashMap;
import java.util.List;
import java.util.Map;

import com.payu.dao.CustomerDAOImpl;
import com.payu.utils.DButils;
import com.wibmo.utils.DBUtils;

/**
 * 
 */
public class StudentDAOImpl implements StudentDAO{
	
	private static volatile StudentDAOImpl instance = null;
	 private StudentDAOImpl() {
	    }
	    
	    public static StudentDAOImpl getInstance() {
	        if (instance == null) {
	        	//synchronized blocks thread safe the object
	            synchronized (StudentDAOImpl.class) {
	                instance = new StudentDAOImpl();
	            }
	        }
	        return instance;
	    }
	    
	    
	    /*****************************************************************/
	    
	private static final Connection conn = DBUtils.getConnection();
	 
	 @Override
	public boolean registerCourse(Long StudentId, List<Integer> CourseIds) {
		
		 return false; 
	}

	@Override
	public void getGrade(Long studentId) {
		// TODO Auto-generated method stub
		
	}

	@Override
	public boolean addCourse(int courseId, Long StudentId) {
		// TODO Auto-generated method stub
		return false;
	}

	@Override
	public boolean dropCourse(int courseId, Long StudentId) {
		// TODO Auto-generated method stub
		return false;
	}

	@Override
	public void viewRegisteredCourses(Long StudentId) {
		// TODO Auto-generated method stub
		
	}

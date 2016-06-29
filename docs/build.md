# build

## References
* http://www.mkyong.com/jdbc/connect-to-oracle-db-via-jdbc-driver-java/

##### Download Oracle JDBC driver
* http://www.oracle.com/technetwork/database/features/jdbc/index-091264.html

##### Add the JDBC driver to the project
* Using Eclipse
  * Project > Properties > Java Build Path > Libraries > Add External JARs

##### Confirm that ojdbc6.jar was added to the project
* Using Eclipse
  * Project > Referenced Libraries
  
##### Make a new class
```java
public class JDBConnector {

}
```

##### Import the java.sql.* package
```java
import java.sql.*;

public class JDBConnector {

}
```
##### Add a main method
```java
public class JDBConnector {

	public static void main(String[] argv) throws ClassNotFoundException, SQLException {
		
	}
}

```

##### Add a try/catch
```java
public class JDBConnector {

	public static void main(String[] argv) throws ClassNotFoundException, SQLException {
			
		try {
		
			Class.forName("oracle.jdbc.driver.OracleDriver");
		
		} catch (ClassNotFoundException e) {
		
			System.out.println("Where is your Oracle JDBC Driver?");
			e.printStackTrace();
			return;
		
		}
	}
}
```

##### Set the Connection object to null
```java
public class JDBConnector {

	public static void main(String[] argv) throws ClassNotFoundException, SQLException {
			
		try {
		
			Class.forName("oracle.jdbc.driver.OracleDriver");
		
		} catch (ClassNotFoundException e) {
		
			System.out.println("Where is your Oracle JDBC Driver?");
			e.printStackTrace();
			return;
		
		}
		
		System.out.println("Oracle JDBC Driver Registered!");
		
		Connection connection = null;
	
	}
}
```

##### Call the getConnection() method of DriverManager to connect to the DB
* Provide hostname/ip address, port, service name, username, and password
```java
public class JDBConnector {

	public static void main(String[] argv) throws ClassNotFoundException, SQLException {
			
		try {
		
			Class.forName("oracle.jdbc.driver.OracleDriver");
		
		} catch (ClassNotFoundException e) {
		
			System.out.println("Where is your Oracle JDBC Driver?");
			e.printStackTrace();
			return;
		
		}
		
		System.out.println("Oracle JDBC Driver Registered!");
		
		Connection connection = null;
	
		try {

			connection = DriverManager.getConnection(
					"jdbc:oracle:thin:@localhost:1521:xe", "system",
					"password");

		} catch (SQLException e) {

			System.out.println("Connection Failed! Check output console");
			e.printStackTrace();
			return;

		}
	}	
}
```

##### Test the connection status and print a message to the console
```java
public class JDBConnector {

	public static void main(String[] argv) throws ClassNotFoundException, SQLException {
		
		try {
		
			Class.forName("oracle.jdbc.driver.OracleDriver");
		
		} catch (ClassNotFoundException e) {
		
			System.out.println("Where is your Oracle JDBC Driver?");
			e.printStackTrace();
			return;
		
		}
		
		System.out.println("Oracle JDBC Driver Registered!");
		
		Connection connection = null;
	
		try {

			connection = DriverManager.getConnection(
					"jdbc:oracle:thin:@localhost:1521:xe", "system",
					"password");

		} catch (SQLException e) {

			System.out.println("Connection Failed! Check output console");
			e.printStackTrace();
			return;

		}
		
		if (connection != null) {
			System.out.println("You made a connection.");
		} else {
			System.out.println("You did not make a connection.");
		}
	}
}
```


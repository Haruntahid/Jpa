>>### Steps of JDBC
>1. import library --> java.sql.*
>2. load and register the driver --> **org.postgresql.Driver**
>3. create connection
>4. create statements
>5. execute query
>6. process the result
>7. close

>> ### Code
```
// importin library
import java.sql.*;

public class JDBC {
    public static void main(String[] args) throws ClassNotFoundException, SQLException{
    // Driver is already loaded and Register
    // Steps:
    // 1. Download from internet(Search as org.postgresql.driver or got to this link [https://jdbc.postgresql.org/download/])
    // 2. In the IntelliJ press CTRL+ALT+SHIFT+S
    // 3. Then nevigate to Modules->Dependancis->Click on Plus Sign
    // 4. Add the Downloaded jar file
    //

        // Connection Starts Here
        String url = "jdbc:postgresql://localhost:5432/test";
        String usrName = "postgres";
        String passWord = "ittertools";

        Class.forName("org.postgresql.Driver"); // Responsible for Driver
        Connection connection = DriverManager.getConnection(url, usrName, passWord);
        // Connection Done

        // Create Statements
        Statement st = connection.createStatement();
        //

        // Executing Query Here
        String query = "select * from stackexchange ;";
        //

        // Processing the result
        ResultSet rs = st.executeQuery(query); // Storing data into rs.
//        rs.next(); // Shifting the pointer
        
        while (rs.next()) { // also work as scan.hasNext() method
            String data = rs.getString("question") + " " + rs.getString("tag") + " " + rs.getDate("date");
            System.out.println(data);
        }
        //

        // Closing Connection
        connection.close();
        //

    }
}

```

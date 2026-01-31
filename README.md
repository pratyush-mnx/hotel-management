# hotel-management
it is an hotel management system used to manage the booking for the hotels 
import java.sql.Connection;
import java.sql.DriverManager;
import java.sql.ResultSet;
import java.sql.Statement;

public class JAVAjdbc_test {

    public static void main(String[] args) {


        String url ="jdbc:mysql://localhost:3306/hotel";
        String user = "root";
        String password = "12345";
        String query = "select * from booking;";



        try{
        Class.forName("com.mysql.cj.jdbc.Driver");
        System.out.println("Driver Loaded");
        }catch(Exception e){
            e.printStackTrace();
        }

        try{
            Connection connection = DriverManager.getConnection(url, user, password);

            System.out.println("Connection Established");

            Statement statement = connection.createStatement();
            System.out.println("Statement Created");
            ResultSet rs = statement.executeQuery(query);
            System.out.println("Query Executed");

            while (rs.next()) {
                int b_ID = rs.getInt("b_ID");
                String name = rs.getString("name");
                String DOB = rs.getString("DOB");
                

                System.out.println(
                        "ID: " + b_ID +
                                ", Name: " + name + ", date: /" + DOB 
                );
            }
            

        }catch(Exception e){
            e.printStackTrace();
        }
    }
}
    


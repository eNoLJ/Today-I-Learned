## MySQL Connector 사용방법

### **1. MySQL Connector 설치**

![image](https://user-images.githubusercontent.com/63284310/106907954-27e8c200-6742-11eb-8900-9e1109125cf3.png)

Looking for previous GA versions? 클릭

![image](https://user-images.githubusercontent.com/63284310/106907964-2ae3b280-6742-11eb-9f63-60f3405ff977.png)

Download 클릭

![image](https://user-images.githubusercontent.com/63284310/106907967-2c14df80-6742-11eb-8a38-e1c80cb90114.png)

No thanks, just start my download 클릭

</br>

### **2. intellij 설정**

Project Structure를 열어 준다.

커맨드 : command + ;

![image](https://user-images.githubusercontent.com/63284310/106909688-df320880-6743-11eb-9593-8372ce0f9604.png)

Libraries 클릭

\+ 클릭

java 클릭

![image](https://user-images.githubusercontent.com/63284310/106909703-e35e2600-6743-11eb-9a81-3bdc27eada07.png)

설치한 MySQL Connector 폴더에 mysql-connector-java-[버전]-bin-jar 선택 후 ok 클릭

</br>

### **3. MySQL Connector 연결 및 사용**

```java
public static void main(String[] args) {
    String server = "localhost"; // MySQL 서버 주소
    String database = "mydb"; // MySQL DATABASE 이름
    String user_name = "eNoLJ"; //  MySQL 서버 아이디
    String password = "123456"; // MySQL 서버 비밀번호

    Connection conn = null;
    Statement stat;
    ResultSet res;

//    1.드라이버 로딩
    public void driverLoding() {
        try {
            Class.forName("com.mysql.jdbc.Driver");
        } catch (ClassNotFoundException e) {
            System.err.println("Driver load error: " + e.getMessage());
        }
    }

//    2. 연결
    public void openConnector() {
        try {
            this.conn = DriverManager.getConnection("jdbc:mysql://" + server + "/" + database + "?useSSL=false", user_name, password);
            this.stat = conn.createStatement();
        } catch (SQLException e) {
            System.err.println("Connector error:" + e.getMessage());
        }
    }

//    3-1. create
    public void insert() {
        String query = "insert into table (column1, column2, column3) values (value1, value2, value3)";

        try {
            stat.executeUpdate(query);
        } catch(SQLException e) {
            System.err.println("Statement error:" + e.getMessage());
        }
    }

//    3-2. read
    public void select() {
        String query = "select * from table";

        try {
            this.res = stat.executeQuery(query);
            while (res.next()) {
                System.out.println(res.getString("id"));
            }
        } catch(SQLException e) {
            System.err.println("Statement error:" + e.getMessage());
        }
    }

//    3-3. update
    public void update() {
        String query = "update table set column1 = value1 where id=1";

        try {
            stat.executeUpdate(query);
        } catch(SQLException e) {
            System.err.println("Statement error:" + e.getMessage());
        }
    }

//    3-4. delete
    public void delete() {
        String query = "delete from table where id=1";

        try {
            stat.executeUpdate(query);
        } catch(SQLException e) {
            System.err.println("Statement error:" + e.getMessage());
        }
    }

//    4. 해제
    public void closeConnector() {
        try {
            if(conn != null)
                conn.close();
        } catch (SQLException e) {}
    }
}

```

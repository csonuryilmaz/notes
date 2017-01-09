With **grep** we can search all files in a directory for a specific text, and list results by file: 

```bash
grep -rnw "/home/onuryilmaz/Downloads/mysql-connector-java-5.1.25-sources" -e "MySQLIntegrityConstraintViolationException"
```

Example output:
```
/home/onuryilmaz/Downloads/mysql-connector-java-5.1.25-sources/com/mysql/jdbc/SQLError.java:40:import com.mysql.jdbc.exceptions.MySQLIntegrityConstraintViolationException;
/home/onuryilmaz/Downloads/mysql-connector-java-5.1.25-sources/com/mysql/jdbc/SQLError.java:1038:						sqlEx = new MySQLIntegrityConstraintViolationException(
/home/onuryilmaz/Downloads/mysql-connector-java-5.1.25-sources/com/mysql/jdbc/SQLError.java:1043:									"com.mysql.jdbc.exceptions.jdbc4.MySQLIntegrityConstraintViolationException",
/home/onuryilmaz/Downloads/mysql-connector-java-5.1.25-sources/com/mysql/jdbc/exceptions/jdbc4/MySQLIntegrityConstraintViolationException.java:29:public class MySQLIntegrityConstraintViolationException extends
/home/onuryilmaz/Downloads/mysql-connector-java-5.1.25-sources/com/mysql/jdbc/exceptions/jdbc4/MySQLIntegrityConstraintViolationException.java:32:	public MySQLIntegrityConstraintViolationException() {
/home/onuryilmaz/Downloads/mysql-connector-java-5.1.25-sources/com/mysql/jdbc/exceptions/jdbc4/MySQLIntegrityConstraintViolationException.java:36:	public MySQLIntegrityConstraintViolationException(String reason, String SQLState, int vendorCode) {
/home/onuryilmaz/Downloads/mysql-connector-java-5.1.25-sources/com/mysql/jdbc/exceptions/jdbc4/MySQLIntegrityConstraintViolationException.java:40:	public MySQLIntegrityConstraintViolationException(String reason, String SQLState) {
/home/onuryilmaz/Downloads/mysql-connector-java-5.1.25-sources/com/mysql/jdbc/exceptions/jdbc4/MySQLIntegrityConstraintViolationException.java:44:	public MySQLIntegrityConstraintViolationException(String reason) {
/home/onuryilmaz/Downloads/mysql-connector-java-5.1.25-sources/com/mysql/jdbc/exceptions/MySQLIntegrityConstraintViolationException.java:27:public class MySQLIntegrityConstraintViolationException extends
/home/onuryilmaz/Downloads/mysql-connector-java-5.1.25-sources/com/mysql/jdbc/exceptions/MySQLIntegrityConstraintViolationException.java:32:	public MySQLIntegrityConstraintViolationException() {
/home/onuryilmaz/Downloads/mysql-connector-java-5.1.25-sources/com/mysql/jdbc/exceptions/MySQLIntegrityConstraintViolationException.java:36:	public MySQLIntegrityConstraintViolationException(String reason, String SQLState, int vendorCode) {
/home/onuryilmaz/Downloads/mysql-connector-java-5.1.25-sources/com/mysql/jdbc/exceptions/MySQLIntegrityConstraintViolationException.java:40:	public MySQLIntegrityConstraintViolationException(String reason, String SQLState) {
/home/onuryilmaz/Downloads/mysql-connector-java-5.1.25-sources/com/mysql/jdbc/exceptions/MySQLIntegrityConstraintViolationException.java:44:	public MySQLIntegrityConstraintViolationException(String reason) {
```

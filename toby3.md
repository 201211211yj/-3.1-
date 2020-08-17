# 3. ���ø�

## 3.1 UserDao ������
UserDao���� ���� �������� �����ִ�. ���ܻ�Ȳ�� ���� ó���� ������ ���� �������̴�.

### ����ó�� ����� ���� DAO
JDBC �ڵ忡�� ����ó���� �ݵ�� ���Ѿ��Ѵ�. �������� JDBC �帧�� ������ �ʰ� �߰��� � �����ε� ���ܰ� �߻����� ��쿡�� ����� ���ҽ��� ��ȯ�ؾ��Ѵ�.

#### JDBC ���� ����� ����ó�� �ڵ�

```java
public void delteAll throws Exception{
	Connection c = dataSource.getConnection();
	
	PreparedStatement ps = c.prepareStatement("delete from users");
	ps.executeUpdate();
	
	ps.close();
	c.close();
}
```

�� �޼ҵ忡���� Connection�� PreparedStatement��� �� ���� ���� ���ҽ��� �����ͼ� ����Ѵ�. ���� ���������� ó���Ǹ� �޼ҵ带 ��ġ�� ���� ���� close()�� ȣ���� ���ҽ��� ��ȯ�Ѵ�. ������ PreparedStatement ó�� ���� ���ܰ� �߻��Ѵٸ� �޼ҵ� ������ ����ġ�� ���ϰ� ����������. �� ��� close() �޼ҵ尡 ������� �ʾ� ����� ���ҽ��� ��ȯ���� ���� �� �ִ�. <br>
�Ϲ������� ���������� ���ѵ� ������ DB Ŀ�ؼ��� ���� ���� ������ Ǯ�� �����Ѵ�. DBǮ�� �Ź� getConnection()���� ������ Ŀ�ؼ��� ��������� close()�ؼ� ������� �ٽ� Ǯ�� �־��ٰ� ���� Ŀ�ؼ� ��û�� ���� �� ������ �� �ִ�. ������ �̷������� ������ �߻��Ǿ� Connection�� ��� ���̰� �Ǹ� ��� ������ Ŀ�ؼ� Ǯ�� ������ �������� ���ҽ��� ���ڶ��ٴ� �ɰ��� ������ ���� ������ �ߴܵ� �� �ִ�. <br>
<br>
**���ҽ� ��ȯ�� close()** 
<br>
Connection�̳� PreparedStatement���� close()�޼ҵ尡 �ִ�. ���� ���ҽ��� ��ȯ�Ѵٴ� �ǹ̷� �����ϴ� ���� ����. �� ���� ���� pool ������� ��ȴ�. �̸� ������ Ǯ �ȿ� ���ѵ� ���� ���ҽ�(Connection, Statement)�� �����ΰ� �ʿ��� �� �̸� �Ҵ��ϰ�, ��ȯ�ϸ� �ٽ� Ǯ�� �ִ� ������� ��ȴ�. ��û�� �ſ� ���� ����ȯ�濡���� �Ź� ���ο� ���ҽ��� �����ϴ� ��� Ǯ�� �̸� ������ ���ҽ��� �������� ����ϴ� ���� �����ϴ�. ��� ����� ���ҽ��� ������ ��ȯ�ؾ��Ѵ�. �׷��� ������ Ǯ�� ���ҽ��� ���� �� �ִ�.
<br>
<br>

�̷� JDBC�ڵ忡���� � ��Ȳ������ ������ ���ҽ��� ��ȯ�ϵ��� try/catch/finally ���� ����� �����Ѵ�. <br>

```java
public void deleteAll() throws SQLException{
	Connection c = null;
	PrepareStatement ps = null;
	
	try{
		c = dataSource.getConnection();
		ps = c.prepareStatement("delete from users");
		ps.executeUpdate();
	} catch (SQLException e) {
		throw e;
	} finally {
		if (ps != null){
			try{
				ps.close();
			} catch (SQLException e){
				//ps.close()�޼ҵ忡���� SQLException�� �߻��� �� �ִ�.
			}
		}
		
		if (c != null){
			try{
				c.close();
			} catch (SQLException e){
			}
		}
	}
}
```


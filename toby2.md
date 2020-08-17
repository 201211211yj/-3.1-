# 2. �׽�Ʈ

## 2.1 UserDaoTest �ٽú���

### UserDaoTest�� Ư¡
�Ʒ� �׽�Ʈ �ڵ�� main() �޼ҵ带 �̿��� UserDao ������Ʈ�� add(), get() �޼ҵ带 ȣ���ϰ� �� ����� ����Ѵ�.<br>
```java
public class UserDaoTest{
	public static void main(String[] args) throws SQLException{
		ApplicationContext context = new GenericXmlApplicationContext("applicationContext.xml");
		
		UserDao dao = context.getBean("userDao", UserDao.class);
		
		User user = new User();
		user.setId("user");
		user.setName("����");
		user.setPassword("hello");
		
		dao.add(user);
		
		System.out.println(user.getId() + "��� ����");
		
		User user2 = dao.get(user.getId());
		System.out.println(user2.getName());
		
		System.out.println(user2.getId() + "��ȸ ����");
	}
}
```

<br>

#### ���� ���� DAO �׽�Ʈ ����� ������
�� ȭ���� ���� ���� �Է��ϰ�, ����� �����ϰ�, ����� Ȯ���ϴ� ����� ���� ���� ���� ��������� DAO��ü�� ���� �׽�Ʈ�δ� ������ ����. DAO�Ӹ� �ƴ϶� ���� Ŭ����, ��Ʈ�ѷ�, JSP �� �� ��� ���̾��� ����� �� ����� ������ �׽�Ʈ�� �����ϴٴ� ���� ���� ū ������. �׽�Ʈ�� �ϴ� �߿� ������ ���ų� �׽�Ʈ�� �����ߵ���, ���� ��𿡼� ������ �߻��ߴ����� ã�Ƴ��� �ϴ� ���� �ʿ��ϴ�. �̷� ������� �׽�Ʈ�ϴ� ���� ������ ���� �� ������ ��Ȯ�ϰ� �����ϱⰡ ����ٴ� ������ �ִ�.

<br>

#### ���� ������ �׽�Ʈ
�׽�Ʈ�ϰ��� �ϴ� ����� ��Ȯ�ϴٸ� �� ��󿡸� �����ؼ� �׽�Ʈ�ϴ� ���� �ٶ����ϴ�. UserDaoTest�� �� ���� ���ɿ� ������ �� �ְ� ���� ������ ������� �׽�Ʈ��. �� �������̽�, MVC Ŭ����, ���� ������Ʈ ���� �ʿ䰡 ����. ������ ������ �ʿ䵵 ����. <br>
�̷��� ���� ������ �ڵ忡 ���� �׽�Ʈ�� ������ ���� ���� �׽�Ʈ(unit test)��� �Ѵ�. ���⼭ ���ϴ� ������ ��������, ũ��� ������ ��� �������� �� ������ �� �ƴϴ�. ����� �ϳ��� ���ɿ� �����ؼ� ȿ�������� �׽�Ʈ�� ���� ������ ������� ���� �ȴ�. <br>

<br>

### UserDaoTest�� ������
* **���� Ȯ�� �۾��� ���ŷο�** : UserDaoTest�� ��� �ڵ����� �����ϵ��� �����������, ������ ����� ������ Ȯ���ϴ� ������ �ʿ��ϴ�. add()���� User ������ DB�� ����ϰ�, �̸� �ٽ� get()�� �̿��� �������� �� �Է��� ���� ������ ���� ��ġ�ϴ����� �׽�Ʈ�ڵ�� Ȯ�������� �ʴ´�.
* **���� �۾��� ���ŷο�** : �ƹ��� ������ ���� ������ main()�޼ҵ�� �ص� �Ź� �װ��� �����ϴ� ���� ���� ���ŷӴ�. ��ü ����� �׽�Ʈ�غ��� ���� main()�޼ҵ带 ���� �� �����ϴ� ���� �ʿ��� ���� �ִ�.

<br>

## 2.2 UserDaoTest ����
### �׽�Ʈ ������ �ڵ�ȭ
ù ��° �������� �׽�Ʈ ����� ���� �κ��� �ڵ�� ������.
```java
public class UserDaoTest{
	public static void main(String[] args) throws SQLException{
		ApplicationContext context = new GenericXmlApplicationContext("applicationContext.xml");
		
		UserDao dao = context.getBean("userDao", UserDao.class);
		
		User user = new User();
		user.setId("user");
		user.setName("����");
		
		dao.add(user);
				
		User user2 = dao.get(user.getId());
		
		if(!user.getName().equals(user2.getName())){
			System.out.println("�׽�Ʈ ���� (name)");
		}else if(!user.getPassword().equals(user2.getPassword())){
			System.out.println("�׽�Ʈ ���� (password)");
		}else{
			System.out.println("�׽�Ʈ ����");
		}
	}
}
```

### �׽�Ʈ�� ȿ������ ����� ��� ����
�� �� ���ϰ� ����� Ȯ���Ϸ��� main()�޼ҵ� �����δ� �Ѱ谡 �ִ�. �ڹٿ��� �ܼ��ϸ鼭�� �ǿ����� �׽�Ʈ�� ���� ������ �������� �����Ѵ�.

#### JUnit �׽�Ʈ�� ��ȯ
�׽�Ʈ�� �����ӿ�ũ�� ���� �����ϰ� �����ν� IoC�� �����Ѵ�.

<br>

#### �׽�Ʈ �޼ҵ��� ��ȯ
���� ���� �� ���� main()�޼ҵ忡 �ִ� �׽�Ʈ �ڵ带 public �޼ҵ�� �����ϰ� @Test ������̼��� �����ش�.
```java
import org.junit.Test;
...
public class UserDaoTest{
	@Test
	public void addAndGet() thorws Exception{
		ApplicationContext context = new ClassPathXmlApplicationContext("applicationContext.xml");
		
		UserDao dao = context.getBean("userDao", UserDao.class);
		...
	}
}
```

<br>

#### ���� �ڵ� ��ȯ
if/else ������ JUnit�� �����ϴ� ����� �̿��� ��ȯ�غ���.
```java
if(!user.getName().equals(user2.getName())){...}
```


```java
assertThat(user2.getName(), is(user.getName()));
```
assertThat()�޼ҵ�� ù ��° �Ķ������ ���� �ڿ� ������ ��ó(matcher)��� �Ҹ��� �������� ���ؼ� ��ġ�ϸ� �������� �Ѿ��, �ƴϸ� �׽�Ʈ�� �����ϵ��� ������ش�.
<br>

```java
import static org.hamcrest.CoreMatchers.is;
import static org.junit.Assert.assertThat;
...
public class UserDaoTest{
	public static void main(String[] args) throws SQLException{
		ApplicationContext context = new GenericXmlApplicationContext("applicationContext.xml");
		
		UserDao dao = context.getBean("userDao", UserDao.class);
		
		User user = new User();
		user.setId("user");
		user.setName("����");
		
		dao.add(user);
				
		User user2 = dao.get(user.getId());
		
		assertThat(user2.getName(), is(user.getName()));
		assertThat(user2.getPassword(), is(user.getPassword()));
	}
}
```
�� �߰��� ���̺귯��
* com.springsource.org.junit

#### JUnit �׽�Ʈ ����
JUnit �����ӿ�ũ�� �̿��� �տ��� ���� �׽�Ʈ �޼ҵ带 �����ϵ��� �غ���.
```java
import org.junit.runner.JUnitCore;
...
public static void main(String[] args){
	JUnitCore.main("spring...UserDaoTest");
}
```
<br>
�� �ڵ带 �����ϸ� ������ ���� �޼����� ��µȴ�.

```
JUnit version 4.7
Time: 0.578
OK (1 test)
```

���� �ڵ忡 �̻��� �־� ������ ������ ��� ������ ���� �޼����� ��µȴ�.

```
Time: 1.094
There was 1 failure:
1) addAndGet(spring...UserDaoTest)
java.lang.AssertionError:
Expected: is "����"
     got: null
     ...
        at spring...UserDaoTest.main(UserDaoTest.java:36)
FAILURES!!!
Tests run : 1, Failures: 1
```

<br>

## 2.3 �����ڸ� ���� �׽��� �����ӿ�ũ JUnit
### JUnit �׽�Ʈ ���� ���

#### IDE
��Ŭ�������� @Test�� ��� �ִ� �׽�Ʈ Ŭ������ ������ �ڿ� Run As - JUnit Test�� �����ϸ� �׽�Ʈ�� �ڵ����� ����ȴ�.
<br>
�׽�Ʈ�� ���۵Ǹ� JUnit �׽�Ʈ ������ ǥ�����ִ� ��(View)�� ��Ÿ���� �׽�Ʈ ���� ��Ȳ�� �����ش�.
<br>
�ҽ� Ʈ���� �����ϰ� Run As - JUnit Test�� �����ϸ� �ش� ��Ű�� �Ʒ��� �ִ� ��� JUnit �׽�Ʈ�� �ѹ��� �������ش�.

#### ���� ��
ANT�� ���̺�(Maven) ���� JUnit �÷����� ���

### �׽�Ʈ ����� �ϰ���
���ݱ��� �׽�Ʈ�� ������ ���� �Ź� UserDaoTest�� �����ϸ� DB�� �����͸� ������� �ߴ�.

#### deleteAll()�� getCount() �߰�
�� deleteAll<br>
```java
public void deleteAll() throws Exception{
	Connection c = dataSource.getConnection();
	
	PreparedStatement ps = c.prepareStatemente("delete from user");
	
	ps.executeUpdate();
	ps.close();
	c.close();
}
```
�� getCount()<br>
```java
public int getCount() throws Exception{
	Connection c = dataSource.getConnection();
	
	PreparedStatement ps = c.prepareStatemente("select count(*) from users");
	
	ResultSet rs = ps.executeQuery();
	rs.next;
	int count = rs.getInt(1);
	
	rs.close();
	ps.close();
	c.close();
}
```

#### deleteAll()�� getCount() �׽�Ʈ
```java
@Test
public void addAndGet() throws Exception{
	...
	dao.deleteAll();
	assertThat(dao.getCount(), is(0));
	
	User user = new User();
	user.setId("hello");
	
	dao.add(user);
	assertThat(dao.getCount(), is(1));
	
	...
}
```

### �������� �׽�Ʈ
�տ��� getCount() �޼ҵ带 �׽�Ʈ�� �����ϱ� ������ �ΰ� �̻��� ���ڵ带 add()���� ���� �� �ɼ��� �ְ����� ��ó �������� ���� ������ ������������ �ִ�.

<br>

#### getCount() �׽�Ʈ

```java
public User(String id, String name, String password){
	this.id = id;
	this.name = name;
	this.password = password;
}

public User(){// �ڹٺ��� �Ծ��� ������ Ŭ������ �����ڸ� ��������� �߰����� ��쿡�� �Ķ���� ���� �����ڵ� �ۼ�������Ѵ�.

}
```

```java
@Test
public void count() throws Exception{
	ApplicationContext context = new GenericXmlAPplicationContext("applicationContext.xml");
	
	UserDao dao = context.getBean("userDao", UserDao.class);
	User user1 = new User("user1", "user1", "user1");
	User user2 = new User("user2", "user2", "user2");
	User user3 = new User("user3", "user3", "user3");
	
	dao.deleteAll();
	assertThat(dao.getCount(), is(0));
	
	dao.add(user1);
	assertThat(dao.getCount(), is(1));
	
	dao.add(user2);
	assertThat(dao.getCount(), is(2));
	
	dao.add(user3);
	assertThat(dao.getCount(), is(3));
}
```

#### addAndGet() �׽�Ʈ ����
```java
@Test
public void addAndGet() throws Exception{
	...
	UserDao dao = context.getBean("userDao", UserDao.class);
	User user1 = new User("user1", "user1", "user1");
	User user2 = new User("user2", "user2", "user2");
	
	dao.add(user1);
	dao.add(user2);
	assertThat(dao.getCount(), is(2));
	
	User userget1 = dao.get(user1.getId());
	asserThat(userget1.getName(), is(user1.getName()));
		
	User userget2 = dao.get(user2.getId());
	asserThat(userget2.getName(), is(user2.getName()));
}
```

#### get() �������ǿ� ���� �׽�Ʈ
```java
@Test(expected=EmptyResultDataAccessException.class)
public void getUserFailure() throws Exception{
	ApplicationContext context = new GenericXmlApplicationContext("applicationContext.xml");
	
	UserDao dao = context.getBean("userDao", UserDao.class);
	dao.deleteAll();
	assertThat(dao.getCount(), is(0));
	
	dao.get("unknown_id"));//�� �޼ҵ� �����߿� ���ܰ� �߻��ؾ� �Ѵ�.
}
```
@Test�� expected�� �߰��س����� expected�� ������ ���� �߻� �� �׽�Ʈ�� �����Ѵ�.

#### �׽�Ʈ�� ������Ű�� ���� �ڵ��� ����
```java
public User get(String id) throws Exception{
	...
	ResultSet rs = ps.executeQuery();
	
	User user = null;
	
	if(rs.next()){
		user = new User();
		user.setId(rs.getString("id"));
		user.setName(rs.getString("name"));
		user.setPassword(rs.getString("password"));
	}
	
	rs.close();
	ps.close();
	c.close();
	
	if(user == null) throw new EmptyResultDataAccessException(1);
	
	return user;
}
```

#### �������� �׽�Ʈ
�׽�Ʈ�� �ۼ��� �� �������� ���̽��� ���� ����� ������ ���̴°� ����. get()�޼ҵ��� ����� �������� �ʴ� id�� �־����� ���� ��� ���������� ���� �����ϰ�, �̸� Ȯ���� �� �ִ� �׽�Ʈ�� ���� ������� �Ѵٸ� ������ ��Ȳ�� ���߸��� ���� ���̴�.

### �׽�Ʈ�� �̲��� ����

#### ��ɼ��踦 ���� �׽�Ʈ
getUserFailure() �׽�Ʈ�� ����� �����غ��� �Ʒ��� ����.<br>
![ex_screenshot](./toby2_screenshot/getUserFailure.jpg)

<br>

#### �׽�Ʈ �ֵ� ����
������� �ϴ� ����� ������ ��������鼭 ������� �ڵ带 ������ ���� �� �ֵ��� �׽�Ʈ �ڵ带 ���� �����, �׽�Ʈ�� �����ϰ� ���ִ� �ڵ带 �ۼ��ϴ� ����� ���� ����� �׽�Ʈ �ֵ� ����(TDD, Test Driven Development)�̶�� �Ѵ�. <br>
TDD�� �ƿ� �׽�Ʈ�� ���� ����� �� �׽�Ʈ�� �����ϵ��� �ϴ� �ڵ常 ����� ������ �����ϱ� ������ �׽�Ʈ�� ������ �ʰ� �Ĳ��ϰ� ���� �� �ִ�. ���� �׽�Ʈ�� �ۼ��ϴ� �ð��� ���ø����̼� �ڵ带 �ۼ��ϴ� �ð��� ������ ª������. <br>
���ݱ��� �����ؿ� ���ߵ� TDD ����̶�� �� �� �ִ�. UserDao�� ����� ������ �׽�Ʈ�� ����鼭 �ڵ带 Ȯ���ؿԴ�. �� ���п� �׽�Ʈ �ڵ带 �߰��� �ۼ��� �ʿ� ���� �ٷιٷ� �׽�Ʈ�غ� �� �־���.

<br>

### �׽�Ʈ �ڵ� ����

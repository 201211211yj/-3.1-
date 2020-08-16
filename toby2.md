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
assertThat()�޼ҵ�� ù ���� �Ķ������ ���� �ڿ� ������ ��ó(matcher)��� �Ҹ��� �������� ���ؼ� ��ġ�ϸ� �������� �Ѿ��, �ƴϸ� �׽�Ʈ�� �����ϵ��� ������ش�.
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

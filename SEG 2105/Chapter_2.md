# Dynamic Binding

Dynamic binding occurs when a decision about which method to run can only be made at run time.

Occurs when:
 - A variable is declared with its type being a super class
 - There is more than one possible polymorphic method can be run

Code examples:

```java
public class SuperClass{
	private int total;
	
	public SuperClass(){
		total = 0;
	}
	public int add(int x){
		return x++;
	}
}

public class SubClass extends SuperClass{
	private SuperClass example;	// Dynamic binding needed
	
	public int add(int x){	// Dynamic binding here too 
		return x + 10; 
	}
}
```


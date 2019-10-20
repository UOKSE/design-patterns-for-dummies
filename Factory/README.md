# Factory Pattern

- A creational design pattern.
- Creates objects without exposing the instantiation logic to the client and
Refers to the newly created object through a common interface.
- Example usage in java core: `java.util.Calendar.getInstance()`

### Sample Implementation

Consider a scenario where in a simple calculator program, we want to create mathematical operation objects dynamically. And we want to seperate instantiation logic of the operation objects from the main code of the calculator program. We can create a common interface called `Operation` which then can be implemented by concrete mathematical operation classes. 

##### Operation Interface:
```
public interface Operation {

    void perform();

}
```
##### AddOperation Class:
```
public class AddOperation  implements Operation{

    @Override
    public void perform() {

        System.out.println("Performing add operation");

    }
}
```
##### SubOperation Class:
```
public class SubOperation implements Operation{

    @Override
    public void perform() {

        System.out.println("Performing sub operation");

    }
}
```
##### DefaultOperation Class:
```
public class DefaultOperation implements Operation {

    @Override
    public void perform() {
        System.out.println("performing the default operation");
    }
}
```

Then we can define a `OperationFactory` class which contains instance initiation logic of the concrete classes and a method to provide relevant operation object when called with an argument. 

##### OperationFactory Class:
```
public class OperationFactory {

    public Operation getInstance(String type){
    
        switch(type)
        {
            case "add" :  return new AddOperation();
            case "sub" :  return new SubOperation();
            default : return new DefaultOperation();
        }
        
    }

}
```
After importing `Operation` interface and `OperationFactory` class to the main code of the program, we can initialize operation objects via `OperationFactory` object without exposing the instantiation logic to the main code. And later if we want to add more operations to the calculator, we can simply add them to the `OperationFactory`, without breaking the logic in the main code of the program. 

```
public class Main {

    public static void main(String[] args) {
        OperationFactory factory = new OperationFactory();
        Operation operation = factory.getInstance("add");
        operation.perform();


    }
}
```






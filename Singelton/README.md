# Singleton Pattern

- A creational design pattern.
- Singleton is used when only one instance of an object is needed throughout
the lifetime of an application.
- Example:
  - Clip Board
  - Windows Registry (System Parameters)
  - Example usage in java core: `java.lang.Runtime#getRuntime()`
  
  ### Implementation: 
  
```  public class Singleton
{
    private static Singleton instance;

    private Singleton()
    {

    }

    public static Singleton getInstance()
    {
        if(instance == null)
            instance = new Singleton();

        return instance;

    }
} 

[Back](BoatProject.md)

```js
/**
 * @author: Alexander Kotzeff, June 29 2020
 * This is a subclass of CrewMember that creates a Captain.
 */

public class Captain extends CrewMember{
  
/**
 * This is the constructor for the Captain subclass. 
 * @param String name sets the name. 
 * @param int age sets the age. 
 */ 
 public Captain(String name, int age){
   super(name, age); 
 }

/**
 * This method states the role of this crew member. 
 * @return String the correct statement. 
 */ 
 public String act(){
   return "The captain is responsible for the crew";
 }

}
```

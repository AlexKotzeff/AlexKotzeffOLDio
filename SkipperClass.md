[Back](BoatProject.md)

```js
/**
 * @author: Alexander Kotzeff, June 29 2020
 * This is a subclass of CrewMember that creates a Skipper.
 */

public class Skipper extends CrewMember{
  
/**
 * This is the constructor for the skipper subclass. 
 * @param String name sets the name. 
 * @param int age sets the age. 
 */ 
 public Skipper(String name, int age){
   super(name, age);
 }

/**
 * This method states the role of this crew member. 
 * @return String the correct statement. 
 */ 
 public String act(){
   return "The skipper is responsible for steering the boat";
 }

}
```

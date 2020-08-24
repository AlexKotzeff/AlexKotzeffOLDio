[Back](BoatProject.md)

```js
/**
 * @author: Alexander Kotzeff, June 29 2020
 * This is an abstract class that acts as a super class to the Captain, Navigator,
 * and Skipper classes.
 */

public abstract class CrewMember{
  
  // create the attributes of the class.
  protected String name;
  protected int age;
  
/**
 * This is the constructor for all crew members on the boat. It sets their name and age. 
 * @param String name takes in the name to set. 
 * @param int age takes in the age to set.
 */
  public CrewMember(String name, int age){
    this.name = name;
    this.age = age;
  }

/**
 * This method is a getter for the name of the crew member.
 * @return String name.
 */
  public String getName(){
    return name;
  }
  
/**
 * This method checks to make sure that two crew members are not the same by compairing names. 
 * @param Object obj takes in the other crew member to check. 
 * @return Boolean True if they are the same. 
 * @return Boolean False if they are not the same. 
 */ 
  public boolean equals(Object obj){
    //Check if the object being compaired to is not stored in the same place in memory and is therefore the same.
    if(this == obj){
      return true;
    }
   
   //if the object being sent to this method is of type CrewMember, compaire the names of the two crew members.
    if (obj instanceof CrewMember){
      CrewMember other = (CrewMember)obj;
      if (this.getName().equals(other.getName())){
        return true;    
      }
    }
    return false;    
  }
 
/**
 * This abstract method is just for subclasses to add to.
 */
  public abstract String act();
  
}
```

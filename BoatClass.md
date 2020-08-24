[Back](BoatProject.md)

```js
/**
 * @author: Alexander Kotzeff, June 29 2020
 * This is an abstract super class that other boat classes can build off of.
 */

import java.util.ArrayList;

public abstract class Boat{
  
  //set the attributes and make an arraylist called crew.
  protected  ArrayList<CrewMember> crew = new ArrayList<CrewMember>();
  private int length;
  private Material material;
  private String name;
  
/**
 * The boat constructor.
 * @param int length in feat
 * @param Material material used for the boat;
 * @param String name of the boat.
 */
  public Boat(int length, Material material, String name){
    this.length = length;
    this.name = name;
    // make a deep copy of the material using the .clone method from Material class.
    this.material = (Material) material.clone();
  }
  
/**
 * this is a getter for the boat name
 * @return name of the boat
 */
  public String getName(){
    return name;
  }

/**
 * this is a getter for the material for the boat
 * @return material
 */
  public Material getMaterial(){
    return material;
  }
  
/**
 * this is a getter for the boat length
 * @return length of the boat
 */
  public int getLength(){
    return length;
  }

/**
 * this is a setter for the boat name.
 * @param String name of the boat
 */
  public void setName(String name){
    this.name = name;
  }

 
/**
 * this is a method to get the list of crew members
 * @return ArrayList<CrewMember>
 */
  public ArrayList<CrewMember> getCrew(){
    return crew;
  }

/**
 * this method calls the act() method for every crew member while printing
 * the actions to the console.
 * @return void
 */
  public void crewToAction(){
    //iterate over the crew arraylist and print the act method.
    for(int i = 0; i < crew.size(); i++){
      String call = crew.get(i).act();
      System.out.println(call);
    }
  }

/**
 * Compairs two boat objects to see if they are the same using its length, name, and material.
 * @param Object obj to receive the object from the user.
 * @return boolean true if the boats are the same.
 * @return boolean false if the boats are not the same.
 */
  public boolean equals(Object obj){
    // since all three of these features of the boat must be the same, they all start as
    // false and are changed to true after being checked indevidually. 
    boolean lengthIsEqual = false;
    boolean nameIsEqual = false;
    boolean materialIsEqual = false;
    
    // make sure the object is of type boat then check each characteristic of the boat.
    if (obj instanceof Boat){
      Boat newBoat = (Boat) obj;
      if(this.getLength() == newBoat.getLength()){
        lengthIsEqual = true;
      }
      if(this.getName().equals(newBoat.getName())){
        nameIsEqual = true;
      }
      //Use the .equals method given in the Material class 
      materialIsEqual = this.getMaterial().equals(newBoat.getMaterial());
      }
    
    // Check all the characteristics and return true if they are all true.
    if(lengthIsEqual == true && nameIsEqual == true && materialIsEqual == true){
      return true;
    }
    return false;
  }
}
```

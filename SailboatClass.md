[Back](BoatProject.md)

```js
/**
 * @author: Alexander Kotzeff, June 29 2020
 * This is a subclass of Boat that creates a sailboat.
 */

class Sailboat extends Boat{
  
  // create new attributes unique to the Sailboat class 
  private double ballast;
  private String keelType;
  
/**
 * Sailboat constructor. 
 * @param int length is boat legth in feat.
 * @param Material material is the boat material
 * @param String name is the boats name
 * @param ballast is the boats ballast capacity in pounds.
 * @param keelType is how the keel is classified.
 */
  public Sailboat(int length, Material material, String name, double ballast, String keelType){
    // send the length, material, and name to the super class constructor
    super(length, material, name);
    
    this.ballast = ballast;
    this.keelType = keelType;
  }
  
/**
 * adds crew members on this boat to an arraylist. Returns true if they are added and false if not.
 * @param CrewMember crewMember to be added.
 * @return boolean true if the crew member was added to the arraylist 
 * @return boolean false if the arraylist already contains the crew member 
 */
  public boolean registerCrew(CrewMember crewMember){
    if(crew.contains(crewMember)){
      return false;
    }
    crew.add(crewMember);  
    return true;
  }

/**
 * finds the Captain in the arraylist of crewmembers
 * @return Captain Captain 
 * @return null if there is no Captain in the arraylist of CrewMembers
 */
  public Captain getCaptain(){
    // iterate through the arraylist of crew members.
    for(int i = 0; i < crew.size(); i++){
      // if the crew member at the location being checked is of type Captain, it is returned.
      if (crew.get(i) instanceof Captain){
        // because we know this CrewMember is a Captain, we can force it to be of type Captain so it can be returned.
        return (Captain)crew.get(i);
      }
    }
    return null;
  }
}
```

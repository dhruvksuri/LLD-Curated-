Assumption: Lift button has direction to go up or down <br/>

Elevator <br/>
  1. Has State, isFanOn, isLightsOn<br/>
  2. Elevator can have a blocking queue (Prod/Con problem)<br/>

State <br/>
  1. Has Direction, currentFloor, Set<Integer> isPressed<br/>

CallElevatorStrategy<br/>
  Elevator getElevator(Elevator[] elevators, Integer currentFloor, Integer destFloor, Integer direction);<br/>
  
ElevatorManager<br/>
   private Elevator[] elevators;<br/>
   private CallElevatorStrategy callElevatorStrategy;<br/>
   callElevator(Integer currentFloor, Integer direction)<br/>
  
NearestCallElevatorStrategy<br/>
  1. Loop each Elevator <br/>
  2. Check if Elevator direction matches with the request direction.<br/>
  3. If Up or Down or Idle, keep track of min distance elevator.<br/>
    

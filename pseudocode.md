# Elevator Code

The Elevator is a used to transport people vertically from and to any floor in this building.
This building had 8 floors.  It has a net capacity of 1500 lbs.  If it is within 10% of the max weight, it will not operate.  A buzzer will alert passengers that it is at an unsafe weight, and some will need to step off and await the next transport.

The primary control for the elevator is inside the elevator cabin itself.  It contains a control panel with 11 buttons (Floors 1 - 8), Door Open, Door Close, and Alarm.  It also has a key to manually shut down operation.  At the top of this panel is a n LCD display which shows the current floor.  The floor buttons contain lights, and will light up when they are selected.

|   |   |
|:---:|:---:|
| 1 | 2 |
| 3 | 4 |
| 5 | 6 |
| 7 | 8 |
|Close | Open |




 an array of floors added to where it needs to stop.  It needs to service each stop in an efficient sequential order, without reversing direction.

Elevator needs to be able to be called from any floor.  If it is called from multiple floors, it needs to be able to add stops, and pick up passengers efficiently.  It doesn't need to pick up passengers who are going the opposite direction.


Doors must be closed before elevator can move.

Doors must not close if they meet resistance to avoid loss of limb and lawsuits to our fine elevator company.

***

START

INIT Variables

    currentFloor
    setFloorUp [Array with 0 position as next]
    setFloorDown [Array with 0 position as next]
    doorsClosed
    goingUp
    callButton [Floor, Direction]

DEFINE Functions

    callElevator()
        What to do when the elevator is called to a floor
    selectFloor()
        What to do when a floor is selected.  If selected inside elevator, floor choice is primary, if set from call button, it is secondary
    whileOpen()
        WHILE doorsClosed = FALSE
            Elevator can't change floors
    myWay()
        Elevator only stops to pick up passengers if they are going same direction as elevator

    isAlarm()
        Elevator will shut down if Fire Alarm is triggered in building

Hitting a button to send the elevator to a specific floor will set setFloor to that floor

If currentFloor is < setFloor, goingUp := True

If the Doors are open, the elevator won't move. This is of critical safety, so needs to have multiple checks.

If currentFloor = setFloor then the elevator needs to stop and the doors open.  doorClosed := False

If goingUp = FALSE elevator needs to stop at all floors 

---

    Var upStopAt []
    Var downStopAt []

    Function selectFloor
        sets floor elevator needs to go to.  If it is Up, adds floor to upStopAt array, else downStopArray

        Use Logic inside elevator, on floor call button, to inputs will be available

    Function callButtonUp
        Input push CONSTfloorValue upStopAt []

    Function callButtonDown
        Input push CONSTfloorValue downStopAt []

    Function cabinButton
        INPUT "BUTTON"
            If BUTTON > currentFloor
                Push BUTTON upStopAt[]
            Else If BUTTON < currentFloor
                Push BUTTON downStopAt[]
            Else
                openDoors

    Function stopAtFloor
        If  goingUp === True
            If upStopAt.includes(currentFloor)
                openDoors
            moveElevatorUp()
        Else
            If downStopAt.contains(currentFloor)
                openDoors
            moveElevatorDown()

    Function moveElevatorUp
        for loop if currentFloor =/ upStopAt [Any Value in Array]
            function moveEleGear(1)

    Function moveElevatorDown
        for loop if currentFloor =/ downStopAt [Any Value in Array]
        function moveEleGear(-1)

    Function openDoors
        Open the doors

    
            

# Elevator Code


Elevator needs to be able to be called from any floor.  If it is called from multiple floors, it needs to be able to add stops, and pick up passengers efficiently.  It doesn't need to pick up passengers who are going the opposite direction.

It also needs to be controlled from inside the cabin.  It needs to be able to have an array of floors added to where it needs to stop.  It needs to service each stop in an efficient sequential order, without reversing direction.

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
            Push BUTTON downStopAt[]

    Function moveElevatorUp
        for loop if currentFloor =/ upStopAt [Any Value in Array]
            function moveEleGear(1)

    Function moveElevatorDown
        for loop if currentFloor =/ downStopAt [Any Value in Array]
        function moveEleGear(-1)
            

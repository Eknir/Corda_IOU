<p align="center">
  <img src="https://www.corda.net/wp-content/uploads/2016/11/fg005_corda_b.png" alt="Corda" width="500">
</p>

# Example CorDapp
Welcome to the example CorDapp. This CorDapp is documented [here](http://docs.corda.net/tutorial-cordapp.html).

## To build this example: 
./gradlew --build-file kotlin-source/build.gradle deployNodes
kotlin-source/build/nodes/runnodes 

## Extra features
As an addition to the standard CorDapp demo, I added the possibility to cancel the IOU. This was done by adding a flow 'Destroyer' and a command 'Destroy'. 

## Manual testing
On the interactive shell of node A: 
1) 'flow start ExampleFlow$Initiator iouValue: 50, otherParty: "O=PartyB,L=New York,C=US"'
2) 'run vaultQuery contractStateType: com.example.state.IOUState' (copy the states.state.data.linearId.id)
3) 'flow start ExampleFlow$Destroyer IOUId: "<copied_id>"'    
4) 'run vaultQuery contractStateType: com.example.state.IOUState' (verify that the state related to the IOU has disappeared)


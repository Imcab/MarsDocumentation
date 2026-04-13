
# Controller bindings

The `ControllerBindings.java` file is used to attach each command to a button of the controller. To help with this, MARS has a model called `Bindings` and the [`ControllerOI`](../bindings/controller-map.md). They can be imported with:

```java
import com.stzteam.mars.models.containers.Binding;
import com.stzteam.mars.operator.ControllerOI;
```

The `ControllerBindings` class implements the `Bindings` interface (also used for test bindings), which is enough to contain all the needed commands with more than one controller, but it is recommended to create a second file with the same structure if more than one is used.

Inside the `bind` method, a var of each group of buttons that will be used is declared, and then each button is assigned to a command. Here is an example where `mechanism` could be substituted with the mechanism you have created and the `setAngle()` is the command you want to run:

```java
package frc.robot;
import com.stzteam.mars.models.containers.Binding;
import com.stzteam.mars.operator.ControllerOI;
import frc.robot.configuration.constants.Constants;
import frc.robot.core.requests.moduleRequests.MechanismRequestFactory;

public class ControlBindings implements Binding {

    private final ControllerOI controller;
    private final Mechanism mechanism = new Mechanism(); 

    public ControlBindings(ControllerOI controller){
        this.controller = controller;
    }

    @Override 
    public void bind(){

    var buttons = controller.getActionButtons();
    var bumpers = controller.getBumpers();
    var leftStick = controller.getLeftStick();
    var rightStick = controller.getRightStick();
    var triggers = controller.getAnalogTriggers();
    var pov = controller.getDPadTriggers();

    buttons
        .top()
        .whileTrue(
            mechanism
                .setControl(
                    () ->
                        MechanismRequestFactory.setAngle() 
                            .withAngle(10)));
    }
    
}
```

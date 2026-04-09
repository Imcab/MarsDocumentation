# Test Routines on Mechanisms

The `MechanismTest` file contains the commands that will conform the test routine for a mechanism. 

## Defining a test

The `@MARSTEST` annotation is used to define a test case for a MARS module. It has a name parameter that specifies the name of the test case.

`Test routine` will be extended as it is a MARS class that allows us to create a routine of commands that will be executed when the test case is selected in the driver station.

The constructor of the test must contain an object of each mechanism that is needed for the test to acces their commands.

Inside of `getRoutineCommand` a `return Commands.sequence()` must be modified to include the sequence of commands that the routine should execute.

### Useful methods for test routines

To have a better control of the test routines, MARS provides some useful methods to create the sequence of commands that will be executed when the test case is selected in the driver station. This methods can be accessed trough the import:

```java
import com.stzteam.mars.test.TestRoutine;
```

- The `sequence()` method is used to create a sequence of commands that will be executed in order.

- The `run()` method is used to execute a command or a sequence of commands when the test case is selected in the driver station. It should return a command that will be executed.

- The `waitFor()` method is used to create a command that will wait for a certain condition to be met before proceeding to the next command in the sequence. It takes a lambda function as a parameter that defines the condition to be met. For example, `waitFor(() -> mechanism.isAtPosition())` will create a command that waits until the mechanism is at a certain position before proceeding to the next command in the sequence.

- The `delay()` method is used to create a command that will wait for a certain amount of time before proceeding to the next command in the sequence. It takes a parameter that specifies in seconds the amount of time to wait in seconds. For example, `delay(2)` will create a command that waits for 2 seconds before proceeding to the next command in the sequence.

Here is an example of a test routine for an arm:

```java
@MARSTest(name = "Arm  Motion Test")
public class ArmTest extends TestRoutine {
  private final Arm a;

  public ArmTest(Arm arm) {
    this.a = arm;
  }

  @Override
  public Command getRoutineCommand() {
    return Commands.sequence(
        run(
            ArmRequestFactory.setAngle()
                .withAngle(-30)
                .withTolerance(Constants.ARM_TOLERANCE),
            a),
        waitFor(() -> a.isAtTarget(Constants.ARM_TOLERANCE), 2),
        delay(1),
        run(
            ArmRequestFactory.setAngle()
                .withAngle(-20)
                .withTolerance(Constants.ARM_TOLERANCE)
            a),
        waitFor(() -> a.isAtTarget(Constants.ARM_TOLERANCE), 2),
        delay(1),
        run(
            ArmRequestFactory.setAngle()
                .withAngle(-8)
                .withTolerance(Constants.ARM_TOLERANCE),
            a),
        waitFor(() -> a.isAtTarget(Constants.ARM_TOLERANCE), 2),
        run(ArmRequestFactory.idle(), a));
  }
}
```

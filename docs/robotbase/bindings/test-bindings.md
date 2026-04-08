
# Test bindings

The `TestBindings` file is used to add the test routines created for the mechanisms to the Elastic chooser in the driver station. This allows to select the test routine we want to execute when the robot is in test mode. To help with this, MARS has a model called `Bindings`, which should be imported with:

```java
import com.stzteam.mars.models.containers.Binding;
```

This `@FunctionalInterface` has a method called `bind` which should be overridden to add the test routines to the Smart Dashboard chooser. This can be done as usual, writing the name as the first parameter and a new instance of the test routine as the second parameter with its defined mechanism as object. For example:

```java
private SendableChooser<TestRoutine> tests = new SendableChooser<>();


public void bind(){
    tests.addOption("Intake Test", new MechanismTest(MechanismObject));

}
````



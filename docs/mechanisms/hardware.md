
# Mechanism IO Real Hardware implementation (Motor)

The `MechanismIOMotor` is used to define the motor you will be using, apply its configurations as normal, and override the declared functions in the `MechanismIO.java` with the desired functionality. Remember that an error will be thrown if you do not override all the declared functions in the `MechanismIO.java` file as this class implements it.

It is recommended to name the file with the name of the mechanism followed by IO and the motory type that will be used. Mind that if the mechanism uses more than one motor you can declare all of them in the same file as long as they perform the same actions as a leader and followers. Otherwise more than one file with each motor type and their own configurations should be created.

Here is an example of a `MechanismIOMotor` file for an arm mechanism using a TalonFX motor:

```java
public class ArmIOKraken implements ArmIO{

    private TalonFX turretAngulator;
    private TalonFXConfigurator turretConfigurator;
    private TalonFXConfiguration talonFXConfigs;

    private MotionMagicExpoVoltage motionRequest;

    public ArmIOKraken(){
        turretAngulator = new TalonFX(ArmConstants.kId, TunerConstants.kCANBus);
        turretConfigurator = turretAngulator.getConfigurator();
        talonFXConfigs = new TalonFXConfiguration();
        motionRequest = new MotionMagicExpoVoltage(0);

        configMotion();
    }

    public void configMotion(){
        var motorConfigs = new MotorOutputConfigs();

        motorConfigs.Inverted = ArmConstants.invertedValue;
        motorConfigs.NeutralMode = NeutralModeValue.Brake;

        var limitConfigs = new CurrentLimitsConfigs();
        limitConfigs.StatorCurrentLimit = ArmConstants.currentLimit;
        limitConfigs.StatorCurrentLimitEnable = true;

        turretAngulator.getConfigurator().apply(limitConfigs);

        talonFXConfigs.Feedback.SensorToMechanismRatio = 0;
        talonFXConfigs.Feedback.RotorToSensorRatio = 1;
        
        var slot0Configs = talonFXConfigs.Slot0;

        slot0Configs.kS = ArmConstants.kS; 
        slot0Configs.kV = ArmConstants.kV; 
        slot0Configs.kA = ArmConstants.kA; 
        slot0Configs.kP = ArmConstants.kP;
        slot0Configs.kI = ArmConstants.kI; 
        slot0Configs.kD = ArmConstants.kD; 

        turretConfigurator.refresh(motorConfigs);
        turretConfigurator.apply(talonFXConfigs);
        turretConfigurator.apply(motorConfigs);
        
    }
    

    @Override
    public void updateInputs(ArmInputs inputs) {

        var rotorPosSignal = turretAngulator.getRotorPosition();

        var rotorPosRotations = rotorPosSignal.getValueAsDouble();
    
        inputs.position = Units.rotationsToDegrees(rotorPosRotations);
        inputs.rotation = Rotation2d.fromRotations(rotorPosRotations);

        inputs.timestamp = rotorPosSignal.getTimestamp().getLatency();

    }

    @Override
    public void applyOutput(double volts) {
        turretAngulator.setVoltage(volts);
    }

    @Override
    public void setPosition(double angle) {
        turretAngulator.setControl(motionRequest.withPosition(Units.degreesToRotations(angle)).withSlot(0));
    }

    
}
```

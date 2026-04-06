# Mechanism color code

MARS allows teams to write status names and match them with a color and a blinking pattern to visualize the status of the mechanism in the official Elastic. This is useful for debugging and for providing feedback to the drivers during a match. To do this, just add to the enum a status following the format:

```java
StatusName(Severity.SeverityExample, DiagnosticPattern.DesiredPattern(Color.DesiredColor))
```

Where:

- `StatusName`: The name of the status. This can be anything that describes the state of the mechanism (Idle, Moving,etc).
- `Severity.SeverityExample`: The severity of the status. This can be: `OK`, `WARNING`, `ERROR`, or `CRITICAL`.
- `DiagnosticPattern.DesiredPattern`: The blinking pattern of the status. This can be: `SOLID`, `BLINK_FAST`, `BLINK_SLOW`, `STROBE`, OR `BREATHING`.
- `Color.DesiredColor`: The color of the status. This can be any color supported by the `edu.wpi.first.wpilibj.util.Color` class.

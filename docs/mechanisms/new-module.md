
# Creating a new module

MARS has a function to quickly create a new module. Just left click over the robot folder and select **MARS: createModule** from the dropdown menu. Then, you will be prompted to enter the name of the module. After you enter the name, MARS will create a new folder with the name of the module which will contain the following files:

1. [**`Mechanism.java`**](../mechanisms/mechanism.md)
2. [**`Mechanism IO.java`**](../mechanisms/io.md)
3. [**`Mechanism request.java`**](../mechanisms/request.md) 
4. [**`Mechanism request factory.java`**](../mechanisms/request-factory.md)
5. [**`Mechanism code.java`**](../mechanisms/code.md)

!!! note
    Some necessary files are not automatically created, meaning you will have to manually create them if you need them (how you decide to organize them is up to you). The files that are not automatically created are below.

    1. [**`MechanismTest.java`**](../mechanisms/test.md). (In case a test routine is needed)
    2. [**`MechanismSim.java`**](../mechanisms/simulation.md) (If you want to add that mechanism to the simulation robot)
    3. [**`MechanismIOMotor.java`**](../mechanisms/hardware.md) (Needs to be created according to the used motor)
   
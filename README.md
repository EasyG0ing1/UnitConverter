# Unint Converter

This is a project that was forked from [@HanSolo](https://github.com/HanSolo) 's project, <a href="https://github.com/HanSolo/converter">Converter</a> which I then added a Builder class to
it and published it so that it can be accessed via live Repository injection
into your project.

## How do I add UnitConverter to my project

The project is available as a Maven dependency on Central. Add the following to your POM file:

```xml
<dependency>
    <groupId>com.simtechdata</groupId>
    <artifactId>UnitConverter</artifactId>
    <version>1.0.0</version>
</dependency>
```

Or, if using Gradle to build, add this to your Gradle build file

```groovy
compile group: 'com.simtechdata', name: 'UnitConverter', version: 1.0.0
```

You can even use it from a Groovy script!

```groovy
@Grapes(
  @Grab(group='com.simtechdata', module='UnitConverter', version=1.0.0)
)
```

## UnitConverter

From the original README <a href="https://github.com/HanSolo/converter">found here</a>:

A Java tool to convert between units. It covers the following categories of units:
 - ACCELERATION
   - METER_PER_SQUARE_SECOND
   - INCH_PER_SQUARE_SECOND
   - GRAVITY
 - ANGLE
   - DEGREE
   - RADIAN
   - GRAD
 - AREA
   - SQUARE_KILOMETER
   - SQUARE_METER
   - SQUARE_CENTIMETER
   - SQUARE_MILLIMETER
   - SQUARE_MICROMETER
   - SQUARE_NANOMETER
   - SQUARE_ANGSTROM
   - SQUARE_PICOMETER
   - SQUARE_FEMTOMETER
   - HECTARE
   - ACRE
   - ARES
   - SQUARE_INCH
   - SQUARE_FOOT
 - DATA
   - BIT
   - KILOBIT
   - MEGABIT
   - GIGABIT
   - BYTE
   - KILOBYTE
   - MEGABYTE
   - GIGABYTE
   - TERABYTE
 - CURRENT
   - PICOAMPERE
   - NANOAMPERE
   - MICROAMPERE
   - MILLIAMPERE
   - AMPERE
   - KILOAMPERE
 - ELECTRIC_CHARGE
   - ELEMENTARY_CHARGE
   - PICOCOULOMB
   - NANOCOULOMB
   - MICROCOULOMB
   - MILLICOULOMB
   - COULOMB
 - ENERGY
   - MILLIJOULE
   - JOULE
   - KILOJOULE
   - MEGAJOULE
   - CALORY
   - KILOCALORY
   - WATT_SECOND
   - WATT_HOUR
   - KILOWATT_SECOND
   - KILOWATT_HOUR
 - FORCE
   - NEWTON
   - KILOGRAM_FORCE
   - POUND_FORCE
 - HUMIDITY
   - PERCENTAGE
 - LENGTH
   - KILOMETER
   - HECTOMETER
   - METER
   - DECIMETER
   - CENTIMETER
   - MILLIMETER
   - MICROMETER
   - NANOMETER
   - ANGSTROM
   - PICOMETER
   - FEMTOMETER
   - INCHES
   - MILES
   - NAUTICAL_MILES
   - FEET
   - YARD
   - LIGHT_YEAR
   - PARSEC
   - PIXEL
   - POINT
   - PICA
   - EM
 - LUMINANCE
   - CANDELA_SQUARE_METER
   - CANDELA_SQUARE_CENTIMETER
   - CANDELA_SQUARE_INCH
   - CANDELA_SQAURE_FOOT
   - LAMBERT
   - FOOT_LAMBERT
 - LUMINOUS_FLUX
   - LUX
   - PHOT
   - FOOT_CANDLE
   - LUMEN_SQUARE_INCH
 - MASS
   - TON
   - KILOGRAM
   - GRAM
   - MILLIGRAM
   - MICROGRAM
   - NANOGRAM
   - PICOGRAM
   - FEMTOGRAM
   - OUNCE
   - POUND
 - PRESSURE
   - MILLIPASCAL
   - PASCAL
   - HECTOPASCAL
   - KILOPASCAL
   - BAR
   - MILLIBAR
   - TORR
   - PSI
   - PSF
   - ATMOSPHERE
 - SPEED
   - MILLIMETER_PER_SECOND
   - METER_PER_SECOND
   - KILOMETER_PER_HOUR
   - MILES_PER_HOUR
   - KNOT
   - MACH
 - TEMPERATURE
   - KELVIN
   - CELSIUS
   - FAHRENHEIT
 - TEMPERATURE_GRADIENT
   - KELVIN_PER_SECOND
   - KELVIN_PER_MINUTE
   - KEVLIN_PER_HOUR
 - TIME
   - WEEK
   - DAY
   - HOUR
   - MINUTE
   - SECOND
   - MILLISECOND
   - MICROSECOND
   - NANOSECOND
   - PICOSECOND
   - FEMTOSECOND
 - TORQUE
   - NEWTON_METER
   - METER_KILOGRAM
   - FOOT_POUND_FORCE
   - INCH_POUND_FORCE
 - VOLUME
   - CUBIC_MILLIMETER
   - MILLILITER
   - LITER
   - CUBIC_METER
   - GALLON
   - CUBIC_FEET
   - CUBIC_INCH
 - VOLTAGE
   - MILLIVOLT
   - VOLT
   - KILOVOLT
   - MEGAVOLT
 - WORK
   - MILLIWATT
   - WATT
   - KILOWATT
   - MEGAWATT
   - GIGAWATT
   - HORSEPOWER
   - JOULE_PER_SECOND

 #Usage

 ```Java
 Converter temperatureConverter = new Converter(TEMPERATURE, CELSIUS); // Type Temperature with BaseUnit Celsius
 double    celsius              = 32.0;
 double    fahrenheit           = temperatureConverter.convert(celsius, FAHRENHEIT);
 double    kelvin               = temperatureConverter.convert(celsius, KELVIN);
 System.out.println(celsius + "??C   =>   " + fahrenheit + "??F    =>   " + kelvin + "??K");


 Converter lengthConverter = new Converter(LENGTH, METER); // Type Length with BaseUnit Meter
 double    meter           = 1.0;
 double    inches          = lengthConverter.convert(meter, INCHES);
 double    nanometer       = lengthConverter.convert(inches, NANOMETER);
 System.out.println(meter + " " + lengthConverter.getUnitShort() + "   =>   " + inches + " in   =>   " + nanometer + " nm");

 // Convert meter to centimeter
 System.out.println(lengthConverter.convertToString(meter, CENTIMETER));

 ```

## Additional Features

### Builder Method

Lets you optionally set the number of decimal places in the output as well as the Locale on a single instantiation line. Those two settings only apply when using the `convertToString` method of the class.

```Java
Converter voltConverter = new Converter.Builder(VOLTAGE, VOLT).decimals(4).locale(Locale.GERMANY).build();
double volts = 1206;
String millivolts = voltConverter.convertToString(volts, MILLIVOLT);
String kilivolts = voltConverter.convertToString(volts, KILOVOLT);
System.out.println(volts + " " + voltConverter.getUnitShort() + " => " + millivolts + " => " + kilivolts);
```

That's basically all it takes to create a very powerful unit converter.

I did my best at documenting the class as much as I could ... thre were a few items I struggled to understand in context and meaning ... but ... it's a great tool that hopefully you will find as useful as I have.

# PlantUML

PlantUML is a software tool used for drawing Unified Modelling Language (UML) diagrams by typing text. This is ideal for storing diagrams in source control systems such as [git](https://git-scm.com). PlantUML can also be used to draw some non-UML diagrams.

UML diagrams you can draw with PlantUML include;

- Activity
- Class
- Component
- Sequence
- State
- Use Case

For information on how to draw these diagrams and other diagrams, please head over to the [PlantUML website](https://plantuml.com).

## PlantUML Server

The fastest and most recommended way to get started drawing PlantUML diagrams is to use the public [PlantUML online server](http://plantuml.com/plantuml). You can use the online server to draw UML diagram in a web browser or connect to it using a PlantUML client such as this [Visual Studio Code extension](https://marketplace.visualstudio.com/items?itemName=jebbs.plantuml).

It is also possible to run your own PlantUML server. For information on how to do this please checkout;

<https://github.com/plantuml/plantuml-server>.

## Command-line and Graphical User Interface

PlantUML can also be run from the command-line. To do this, you will need the following prerequisites installed on your local machine;

- Java
- [Graphviz](https://graphviz.org)

PlantUML is distributed as a Java JAR file which you can download from <https://plantuml.com/download>.

The following is an example of how to run PlantUML from the command-line;

    java -jar plantuml.jar MyDiagram.txt

This will output a file called `MyDiagram.png` in the same directory as the file `MyDiagram.txt`.

PlantUML also has a [Graphical User Interface (GUI)](https://plantuml.com/gui) which you can open by running;

    java -jar plantuml.jar -gui

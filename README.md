# New README

1. Install `Phosphor` (0.0.5 is the latest version) by cloning and running `mvn install`. The `Phosphor-0.0.5-SNAPSHOT.jar` file will be installed under `~/.m2/repository...`
2. Clone this repo somewhere.
3. Under this repo's target folder, create instrumented copy of JRE using slight variation of the following command:
    - `java -jar Phosphor-0.0.5-SNAPSHOT.jar /Library/Java/JavaVirtualMachines/jdk1.8.0_222.jdk/Contents/Home jre-inst`
    Change the JRE location and pass full path of the Phosphor jar (or better yet, copy that jar in the target folder, and run this from the target folder).
4. Run `mvn compile` from the main folder to compile the package.
5. Go back to the target folder, and run this: `./jre-inst-obj/bin/java -ea  -Xbootclasspath/a:Phosphor-0.0.5-SNAPSHOT.jar -javaagent:Phosphor-0.0.5-SNAPSHOT.jar -cp ./classes/ com.josecambronero.IntegerTagExamples`

Currently only the IntegerTagExamples code has been modified to work (first 4 tests). Similar modifications can be made to other tests. Note that it seems that v0.0.5 of Phosphor does not have the `Tainter` class anymore, and there's only `MultiTainter`. So the code has been modified slightly.

----------

### Info
This simple project is meant to be a series of example showing how to use
Phosphor. Bear in mind that I created this in the process of learning
how to use Phosphor myself, so there are bound to be mistakes/inefficiencies in the examples.
These are solely my responsibility and should not be viewed as a reflection of anyone elses work.


### Running
In order to run the examples, you must download the Phosphor project and build it.
See [Phosphor](https://github.com/Programming-Systems-Lab/phosphor) for more information. 
Running `mvn install` as done below will create the 
Phosphor jar and instrument various JREs which the examples rely upon.

```
cd /path/to/Phosphor/project
mvn install # put jar in maven local repository
cd /path/to/phophor-examples
mvn package # creates jar with examples)
./run_examples.sh <folder-instrumented-jre-and-phosphor-jar> # see ./run_examples.sh -h
```

(I'm sure there is a nicer way of doing this with maven, but I'm not as familiar with it,
so feel free to modify and put in a PR if you are)

If you'd like to read along with the notes I made for this project, run
`mvn latex:latex` which creates a pdf report at target/site/notes.pdf
# Subtyping (Interfaces)

*Deutsch: Schnittstellen(typen) und Untertypenbeziehung*

In Java gibt es zwei Möglichkeiten, Typen zu deklarieren
- Class (Klassentypen)
- Interface (Schnittstellentypen)

*In Java ist die Verwendung mehrerer Superklassen nicht gestattet - wenn eine Klasse also mehrere Supertypen haben soll, müssen Interfaces verwendet werden.*

**Class:** deklariert neuen Typ zusammen mit der Implementierung
**Interface**: deklariert neuen Typ, legt aber nur öffentliche Schnittstelle des Typs fest (besitzt keine eigene Implementierung und keine "eigenen" Objekte)



## Interface

`Student` ist ein Subtyp von `Printable`. Die Implementierung von `Student` ist eine der Implementierungen des Typs `Printable`.

```java
interface Printable {
	void print();
}
```
```java
class Student implements Printable {
  ...
	public void print(){...}
}
```



#### Deklaration von Schnittstellentyp (Interface)

Legt folgendes fest:

- Typname
- Namen bekannter Konstanten
- erweiterte Signaturen der Methoden, die der Typ zur Verfügung stellt

```java
interface Person {
	String getName();
	int getBirthdate();
	boolean hasBirthday(int date);
}
```



#### Typ: Class oder Interface?

###### Wann bietet sich die Implementierung als Interface an?

- nur sehr wenig Wissen über einen Typ
- wollen uns auf keine Implementierungsaspekte festlegen

Kommt eher am "oberen Ende" von Typhierarchien vor (also bei den allgemeinen, abstrakten Typen).

###### Wann bietet sich die Implementierung als Class an?

- Typ soll auch ohne Subtypen angewendet werden
- Typ soll mit Implementierung versehen werden

Die Implementierung kann in Subklassen spezialisiert werden. Durch Vererbung von Implementierungsteilen kann viel an Programmierarbeit gespart werden.



## Subtyping

```java
class PrintWithCount{
    private static void count = 1;
    
    public static void nrPrint(Printable printable){
        System.out.println("Count" + count + ":");
        printable.print();
        count++;
    }
}
```

In  `nrPrint()` wird die Methode `print()` aus dem Interface `Printable` aufgerufen. Das Interface selbst hat keine Implementierung der Methode. Die Implementierungen sind in den Subtypen des Interfaces beschrieben. 

Aufgrund von **dynamischer Bindung** wird jeweils die Methode des Subtyps aufgerufen. In der Zeile `printable.print()` kommen also verschiedene Methoden zur Ausführung.

Zur Compiletime (Übersetzungszeit) ist nicht sicher, welcher Programmcode ausgeführt wird. Das kann erst zur Runtime (Laufzeit) des Programms bestimmt werden.

##### Subtyping zusammengefasst

> Typ B wird als Subtyp vom Typ A bezeichnet, wenn eine Instanz von B in jeder Situation verwendet werden kann, in der eine Instanz von A erforderlich ist.

- erlaubt es, gemeinsame Eigenschaften unterschiedlicher Typen in Form eines allgemeinen Typs auszudrücken

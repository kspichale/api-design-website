---
layout: page
title: Errata
---
Wenn Sie einen Fehler im Buch finden, können Sie mir diesen gerne per E-Mail an [kai.spichale@api-design.de](mailto:kai.spichale@api-design.de) schicken. Ich bemühe mich, die Fehler an dieser Stelle aktuell zu halten und vor dem nächten Druck zu korrigieren.

## 1. Auflage, Druck 2016
Die folgenden Fehler wurde bereits im Nachdruck 2017 korrigiert.

Ich bedanke mich bei Prof. Dr. Dominik Gruntz für sein umfangreiches Feedback.

### Kapitel 3

Auf **Seite 30** findet man im Quelltextbeispiel die Methode *create()*, die korrekterweise *build()* hätte heißen müssen.

### Kapitel 5

Auf **Seite 69** ist das Quellcodebeispiel unvollständig, denn es fehlt der Rückgabewert im Fall einer Exception. Als Rückgabewert eignet sich *null* oder eine leere Liste, wie dies hier gezeigt ist. Die leere Liste wird bevorzugt, weil sie hilft, NullPointerExceptions beim Aufrufer der Methode zu vermeiden.

```
public List<Bookings> getBookings() {
	try {
		// ...
	} catch (IOException|SQLException ex) {
		logger.log(ex);
		return Collections.emptyList();
	}
}
```

Auf **Seite 80** wird fälschlicherweise behauptet, das Unterbinden von Vererbung hieße bei Java "Sealing". In der [offiziellen Dokumentation](https://docs.oracle.com/javase/tutorial/deployment/jar/sealman.html) wird der Begriff jedoch nur für Packages verwendet, die vollständig innerhalb derselben JAR-Datei liegen müssen. Der Begriff Sealing, wie er im API-Buch verwendet wird, ist aber dennoch nicht unüblich.

### Kapitel 6

Auf **Seite 97** ist der Name des Future-Objektes im unteren Quellcodebeispiel falsch. Das Beispiel müsste folgendermaßen lauten:

```
int result = handle.get(5, TimeUnit.SECONDS);
```

Auch auf **Seite 98** ist der Name des Future-Objektes im oberen Quellcodebeispiel falsch. Das Beispiel müsste folgendermaßen lauten:

```
boolean isDone = handle.isDone();
```

Auf **Seite 99** steht, dass das Projekt http://immutables.github.io bereits erwähnt wurde. Das Projekt wird jedoch erst auf Seite 112 vorgestellt.

Auf **Seite 117** ist das Quellcodebeispiel falsch, korrekt wäre:

```
public class ThisEscape {
	private State[] states = new State[] {
		new State(...), ...
	};
	
	public ThisEscape (Collection<ThisEscape> register) {
		register.add(this);
		// weitere Initialisierung
	}
	
	public State[] getStates() {
		return states;
	}
}
```

### Kapitel 7

Auf **Seite 127** wird die Annotation @Deprecated genannt, jedoch fälschlicherweise kleingeschrieben. Dieser kleine Unterschied ist wichtig, denn @deprecated ist ein Tag von JavaDoc, das aber an dieser Stelle nicht gemeint ist.

Auf **Seite 129** ist das Quellcodebeispiel falsch. Der korrigierte Quellcode für die Klasse *Shape* lautet:

```
public Shape extends AbstractShape implements Drawable {
	public static void main(String[] args) {
		Shape s = new Shape();
		System.out.println(s.identifyMyself());
	}
}	
```

Auf **Seite 134** steht fälschlicherweise geschrieben, dass das Interface java.util.Iterator um die Methode *remove* erweitert wurde. Diese Aussage ist falsch, denn die Methode gibt es bereits seit Version 1.2. Mit Java 8 wurde der Methode lediglich eine Default-Implementierung spendiert, um zukünftige Implementierungen des Interfaces zu vereinfachen.

### Kapitel 8

Auf **Seite 153** steht fälschlicherweise, dass ein Client bei HTTP PUT mithilfe eines Location-Headers die URI der neuen Ressource bestimmt. Vielmehr wird bei PUT die URI mithilfe der URL der Ressource, auf der das PUT ausgeführt wird, definiert. Der Location-Header identifiziert die Ressource nach einem POST.

Auf **Seite 159** wurde in der Tabelle die Bedeutung von next und previous vertauscht.

### Kapitel 9

Auf **Seite 167** und **Seite 168** wird zur Aktualisierung der erzeugten Ressourcen POST genannt, weil damit beliebige Verarbeitungen angestoßen werden können. Für Aktualisierungen wäre jedoch auch idempotente PUT-Aufrufe ausreichend.

Auf **Seite 170** wurde in der Abbildung 9-6 'Colleciton' falsch geschrieben.

Auf **Seite 174** steht fälschlicherweise hinter %20 ein 's'.

Auf **Seite 190** wird als Beispiel für den Statuscode 204 ein erfolgreicher DELETE-Aufruf genannt. Für nachfolgende Anrufe der gelöschten Ressource sollte jedoch besser der Statuscode 410 Gone verwendet werden. Ein anderes Beispiel für die Verwendung von Statuscode 204 ist ein erfolgreich durchgeführter PUT-Aufruf, dessen Antwort keine Entität enthält.

### Kapitel 10

Auf **Seite 213** gibt es einen Platzhalter im Text, der nicht ersetzt wurde. Die Klammerbemerkung (Latest SOAP versions) müsste entfernt werden.

Auf **Seite 216** in der Abbildung 10-1 fehlt eine Pfeilspitze bei der Referenz von *binding* auf *portType*.

### Kapitel 11

Auf Seite **248** müsste der zweite Absatz folgendermaßen beginnen: "Im dritten und vierten Fall werden Transaktionen mit Funktionen wie Commit und Rollback, ähnlich wie bei JDBC, eingesetzt."

### Kapitel 15

Auf **Seite 313** ist das Akronym falsch. Es heißt korrekterweise "YAGNI".

Auf **Seite 315** ist dieser Satz sprachlich falsch: "Dieses Beispiel zeigt einen Komponententest gezeigt."

### Kapitel 16

Auf **Seite 326** heißt es: "Zur Beschreibung von APIs eignen sich spezielle Dokumentations- und Modellierungssprachen, die in Kapitel 12 genauer vorgestellt werden." Der Satz müsste korrekt lauten: "Zur Beschreibung von APIs eignen sich spezielle Dokumentations- und Modellierungssprachen, die in Kapitel 12 genauer vorgestellt wurden."
1. Welche Stufen gibt es bei der **Wissenstreppe**?  
    Nennen Sie diese der Reihe nach und machen Sie ein Beispiel mit einem Wechselkurs.
	
	
2. Wie werden **Netzwerk-Beziehungen** im **logischen** Modell abgebildet?
	- **Entitäten:** _Repräsentiert Objekte über welche Daten gespeichert werden sollen._
	- **Beziehungstypen:** _Zeigt wie einzelne Objekte miteinander verbunden sind. Beziehungstypen sind 1:1, 1:n, n:m_
	- **Attribute:** _Sind Eigenschaften von Entitäten und tragen zur Beschreibung der Daten bei. Jede Entität und jeder  Beziehungstype kann verschiedene Attribute haben._
	- **Schlüssel:** _Schlüssel sind Attribute oder eine Kombination von Attributen, die eine Entität eindeutig identifiziert. Jede Entität sollte einen eindeutigen Schlüssel haben (UUID)._
	
1. Was sind **Anomalien** in einer Datenbasis? Welche Arten gibt es?
	 _Anomalien in einer Datenbasis sind unerwartete oder ungewöhnliche Zustände oder Ereignisse, die von den normalen Betriebsbedingungen abweichen und potenziell Fehler oder Probleme in den Daten signalisieren_.
	 
	_Zum Verhindern:
	- _3. Normalform_
	- _Redundanz_
	- _Ref. Integrität_
	
4. Gibt es redundante "**Daten**"? Warum?
	_Ja redundante Daten können in einer Datenbank aus verschiedenen Gründen vorhanden sein:_
	- _Mehrere Speicherorte_
	- _Denormalisierung_
	- _Fehlerhafte Datenbankdesigns_
	- _Synchronisationsprobleme_
	- _Historische Daten_
		
5. **Datenstrukturierung**:  
    Welche zwei Aspekte können strukturiert werden?  
    
    _Logische Struktur_
    _Physische Struktur_
    
    Welche Kategorien (Abstufungen) gibt es bei der Strukturierung?  
    
    _Datenmodellierung_
    _Normalisierung_
    _Indexierung_
    _Partitionierung_
    _Denormalisierung_
    
    Und wie müssen die Daten in einer DB strukturiert sein?
    
    _Daten in einer Datenbank müssen gemäss einem klaren Datenmodell logisch strukturiert sein. Beispiele für Datenmodelle sind das relationale Modell(Tabellen und Beziehungen), hierarchische Modelle (Baumstruktur) und objektorientierte Modelle._
    
    _Die physische Struktur beinhaltet Aspekte wie die Anordnung von Datensätzen, Indizierung zur Beschleunigung des Datenzugriffs und die Organisation auf der Festplatte._
	
	
6. Beschreiben das Bild mit den richtigen Fachbegriffen[![Terminologie](https://gitlab.com/ch-tbz-it/Stud/m164/-/raw/main/10_Auftraege_und_Uebungen/00_Start/Recap_Fragen/Tabelle_labelled.png)](https://gitlab.com/ch-tbz-it/Stud/m164/-/raw/main/10_Auftraege_und_Uebungen/00_Start/Recap_Fragen/Tabelle_labelled.png)
	1. _Entität_
	2. _UUID_
	3. _Attributnamen_
	4. _Attribute_
	5.  _?_
	
	
7. Welche (einschränkenden) **Einstellungen** zu den Attributen (z.B. ID) kennen Sie?
	- _Primary Key_
	- _Unique Constraint_
	- _Foreign Key_
	- _Check Constraint_
	- _Default Value_
	- _Not Null Constraint_
	- _Indexierung_
[![Constriant](https://gitlab.com/ch-tbz-it/Stud/m164/-/raw/main/10_Auftraege_und_Uebungen/00_Start/Recap_Fragen/WB_Constraints.png)](https://gitlab.com/ch-tbz-it/Stud/m164/-/raw/main/10_Auftraege_und_Uebungen/00_Start/Recap_Fragen/WB_Constraints.png)
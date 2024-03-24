# Chapter 1
1. Arten von Unterprogrammen
* Offenes Unterprogramm -> Code wird direckt ins Hauptprogramm kopiert.
* geschlossenes Unterprogramm(Prozedur) -> Man sprint aus dem Hauptprogramm an die Stelle der Prozedur.
  
2. **Register, PC(Rücksprungadresse), Parameter, Ergebnis** werden in die Stack gespeichert.
  
3. Geben Sie die aus der Vorlesung Rechnerarchitektur bekannte vierstufige Aufrufkonvention
an, die ein korrektes Zusammenarbeiten von Hauptprogramm und Unterprogramm mit Hilfe
des Stacks gewährleistet. Geben Sie zu jedem der vier Aufrufe an, welche der in Aufgabe ??)
genannten Zustandsinformationen jeweils verarbeitet werden.

4. 4-stufige Aufrufkonvention:
* Prolog des Callers: Register, Rücksprungadresse, Parameter auf den Stack.
* Prolog des Callees: Parameter runter und Code durchzuführen.
* Epilog des Callees: Rücksprungadresse runter, Ergebnisse auf den Stack
* Epilog des Callers: Ergebnis vom Stack, Register runter.

5. Anweudungsprogramme / Betriebsystem / Hardware

6. 

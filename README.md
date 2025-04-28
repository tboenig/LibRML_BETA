# LibRML_BETA

Library Rights Machine-readable Language (kurz LibRML)

LibRML_Beta möchte die Arbeiten an einem LibRML-Schema, die in der SLUB - Sächsische Landesbibliothek — Staats- und Universitätsbibliothek Dresden begonnen wurden, fortsetzen. Zu einem späteren Zeitpunkt können die Arbeiten an der SLUB mit diesen Arbeiten zusammengeführt werden.
LibRML_Beta nutzt vorerst das an der SLUB entwickelte XSD-Schema. Das Repository kann auch als Diskussionpunkt für ein LibRML Schema genutzt werden.

# LibRML-Original
Zur Information des LibRML-Entwurfes 
- GitHub: https://github.com/slub/librml
- Internet: https://librml.org/



## Inhalt

- [XML-Schema](#xml-schema)
- [Elemente und Typen](#elemente-und-typen)
- [Einschränkungen](#einschränkungen)
- [Verwendung](#verwendung)
- [Feedback und Beiträge](#feedback-und-beiträge)



## XML-Schema

Das originale SLUB-LibRML-Schema und das LibRML-Beta-Schema finden Sie im Repositorium.
Das zentrale LibRML-Beta-Schema enthält:
- Typisierte Elemente und Attribute.
- Reguläre Ausdrücke für die Validierung von IPv4-, IPv6- und MAC-Adressen.
- Einschränkungen über `xs:assert` .

## Elemente und Typen

### Hauptstruktur
- `libRML`: Wurzelelement des Schemas.
  - Attribut: `version`

### Typen
1. **libRMLType**
   - Container für alle untergeordneten Elemente.
   - Enthält das Element `item`.


2. **ItemType (item)**
   - Beinhaltet Aktionen (`action`).
   - Enthält das Attribute `id`, `tenant`, `mention`, `sharealike`, `commercialuse`, `copyright`, `template`, `usageguide`
   
3. **ActionType**
   - Beinhaltet Restriktionen (`restriction`) mit Typen wie `displaymetadata`, `read`, `run` usw.
   - Attribute wie `type` und `permission`.

4. **RestrictionType**
   - Validierung für `subnet`, `machine`, `part`, und Attribute wie `fromdate`, `todate`, `maxresolution`, etc.
   - Unterstützt reguläre Ausdrücke für IP-Adressen und MAC-Adressen.

## Einschränkungen

Das Schema (XSD-Version 1.1) verwendet `xs:assert`, um logische Regeln und Einschränkungen auf Attribute und untergeordnete Elemente anzuwenden, wie:
- Verhinderung inkompatibler Kombinationen von Aktionen und Restriktionen.
- Validierung spezifischer Szenarien basierend auf Attributen wie `type`, `date`, oder `age`.

Damit ist das Schema bei der Formulierung von Instanzen "streng".

Die Verwendung von XSD-Schema 1.1 hat Vor- und Nachteile:
- Vorteil:
  - einfache Formulierung von Präzisierungen, Abhängigkeiten und Verwendungen von Elementen und Attributen
  - Formulierung in XPath
 
- Nachteil:
  - `xs:assert` erst ab der XSD-Version 1.1 verwendbar.
  - Parser muss XSD-1.1 kompatibel sein.
 
- Alternativen
  - `xs:assert` in Schematronregeln umsetzen.
  - Schematron aus dem XSD automatisiert erstellen.

## Verwendung

1. Lade die `LibRML-BETA.xsd` herunter und importiere sie in deinen XML-Validierungsprozess.
2. Verwende Tools wie Oxygen, XMLSpy, XSDValidator oder eingebettete Validatoren, um das Schema zu verändern oder XML-Dokumente gegen das Schema zu validieren.


## Feedback und Beiträge

Wir freuen uns über Feedback und Vorschläge zur Verbesserung der Bibliothek! Erstelle dazu bitte ein **Issue** im Repository oder reiche einen **Pull-Request** ein.

---


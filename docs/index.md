# CiviCRM Ressourcenverwaltung (de.systopia.resource)

## Einleitung

Die Verwaltung von Ressourcen in CiviCRM erfordert oft individuelle
Konfigurationen und Tools. CiviVolunteer bietet einige passende Features, hat
aber auch vordefinierte Workflows, die schwer anzupassen oder zu erweitern sind.
Die Verwendung von physischen Ressourcen war schon immer kompliziert - wir haben
viele Kontaktunterarten gesehen, die "Projektor" "Raum" usw. heißen....
Vor allem Freiwilligenorganisationen müssen in der Lage sein, die
Qualifikationen ihrer Unterstützer*innen im Detail zu verfolgen und
Möglichkeiten für die Einsätze von Freiwilligen zu verwalten.
Engagementmöglichkeiten können eine Reihe von Ressourcen erfordern (sowohl
personelle als auch materielle Ressourcen). Wenn man zum Beispiel eine
Veranstaltung organisiert, benötigt man eine bestimmte Anzahl von Helfer*innen,
medizinisches Personal, ein Fahrzeug, Projektoren und vieles mehr.
Da dies je nach Anwendungsfall und Größe der Organisation ziemlich komplex
werden kann haben wir das hier vorgestellte Framework geschaffen. Es ermöglicht
das Managen von Ressourcenbedarfen, Ressourcen und ihren Verfügbarkeiten und
bietet Mechanismen für deren Matching.
Diese Erweiterung kann einzeln verwendet werden, aber für viele Anwendungsfälle
kann es sinnvoll sein, sie mit anderen unten beschriebenen Erweiterungen zu
integrieren.
Die Erweiterung ist lizenziert unter
[AGPL-3.0] (https://github.com/systopia/de.systopia.resource/blob/master/LICENSE.txt)
.

## Umfang & Funktionen

### [Ressourcenmanagement-Erweiterung](https://github.com/systopia/de.systopia.resource)

Die Haupterweiterung bietet eine Benutzeroberfläche, um Ressourcen und Bedarfe
zu definieren und einen Algorithmus, um diese zu matchen. Wenn eine Ressource
einem Bedarf zugewiesen wird, wird sie für die angegebene Zeitspanne geblockt.
Es können auch allgemeinen Verfügbarkeitsbeschränkungen für Ressourcen
hinterlegt werden (z.B. Urlaube).
Für jeden Ressourcenbedarf können Bedingungen angegeben werden, insbesondere in
welchem Zeitrahmen die Ressource benötigt wird, aber auch andere Bedingungen wie
Gruppen, denen die Ressource angehören muss, und vieles mehr.
Die Erweiterung schlägt Ressourcen vor, die den definierten Bedarfen
entsprechen, und ermöglicht es, diese einander zuzuweisen. Auch einige
Funktionen zur Onlineintegration sind bereits implementiert (v.a. das Einladen
von Kontakten zur Teilnahme an einer passenden Gelegenheit) - vieles mehr ist
für die Zukunft geplant.

### [Entity Construction Kit](https://github.com/systopia/de.systopia.eck)

Diese Erweiterung ermöglicht es, benutzerdefinierte Entitäten über die
Benutzeroberfläche von CiviCRM zu erstellen und Entitäten benutzerdefinierte
Felder zuzuweisen. Im Zusammenhang mit der Ressourcenverwaltung benötigt man sie
nur, wenn physische bzw. "nicht-CiviCRM-Kontakt-Ressourcen" verwalten werden
sollen wollen.
Für diesen Fall würde man einen benutzerdefinierten Entitätstyp und/oder
Untertypen für jede Ressourcenkategorie erstellen, die man verwalten möchten.

### Search Kit

Das Search Kit ist eine CiviCRM (Core-)Erweiterung und erlaubt es, diverse
Suchen, Listenansichten und vieles mehr zu erstellen. Da das Entity Construction
Kit selbst nur eine begrenzte Benutzeroberfläche bietet, muss man das Search Kit
verwenden, um benutzerdefinierte Entitäten zu finden, zu erstellen und zu
bearbeiten.
Wenn man nur Kontaktressourcen verwaltet, benötigt man das Search Kit nicht
unbedingt, aber es kann ggf. helfen, deutlich bessere Suchen und Ansichten zu
erstellen.

### [Ressourcen-CiviEvent-Integration](https://github.com/systopia/de.systopia.resourceevent)

Vereinfacht gesagt erstellt diese Erweiterung immer eine spezielle
Event-Anmeldung, wenn eine Ressource einem Bedarf zugewiesen wird uns
sychronisiert diese. Es wird also der Status der Anmeldung geändert, wenn die
verknüpfte Ressourcenzuweisung bearbeitet wird bzw. die Ressourcenzuweisung
geändert wenn die Anmeldung bearbeitet wird.
Diese Erweiterung ist nicht erforderlich, aber in vielen Fällen sehr nützlich.
Dadurch dass man eine Anmeldung für jede Ressourcenzuweisung hat, kann man bspw.
viele Kernfunktionen (wie Suchen und Berichte zum Filtern von Zuordnungen)
nutzen, für die Sie sonst benutzerdefinierte Funktionen verwenden müssten.
Darüber hinaus kann man zudem auf die ständig wachsende Anzahl von Erweiterungen
für CiviEvent zurückgreifen wie
[Event Messages] (https://github.com/systopia/de.systopia.eventmessages),
[Event Invitation] (https://github.com/systopia/de.systopia.eventinvitation),
[Event Checkin] (https://github.com/systopia/de.systopia.eventcheckin) oder
[Remote Events] (https://github.com/systopia/de.systopia.remoteevent). Dies
ist besonders nützlich, wenn man plant, Onlineintegrationen für Freiwillige
anzubieten.

### [Einladungserweiterung](https://github.com/systopia/de.systopia.eventinvitation)

Diese Erweiterung ermöglicht es, Kontakte in CiviCRM zu einer Veranstaltung
einzuladen und bietet ein einfaches Feedback-Formular, in dem die Kontakte
wählen können, ob sie teilnehmen möchten oder nicht. Wenn man die Erweiterung "
Ressourcen-CiviEvent-Integration" verwendet, erweitern sich die möglichen
Anwendungsfälle und man kann bspw. Kontakte /Freiwillige zur "Teilnahme als
Ressource" für einen bestimmten Bedarf einladen. Man benötigen diese Erweiterung
nur, wenn man diese Funktion nutzen möchte.

### Anmerkungen & Einschränkungen

Die Architektur der Erweiterung wurde mit Blick auf ziemlich komplexe
Anwendungsfälle entwickelt, aber wir haben versucht, sie so zugänglich wie
möglich für weniger komplizierte Szenarien zu machen. Derzeit können die
UI-Funktionen nur in Kombination mit CiviEvent verwendet werden. Es ist gut
möglich, dass in Zukunft alle oder einige Funktionen auch eigenständig verfügbar
gemacht werden.
Wir planen derzeit eine zweite Projektphase, die sich voraussichtlich auf die
Onlineintegration unter Verwendung der Funktionen
von [Remote Events] (https://github.com/systopia/de.systopia.remoteevent)
und [Remote Tools] (https://github.com/systopia/de.systopia.remotetools) und die
Integration mit Drupal9 unter Verwendung von
[CiviMRF] (https://github.com/CiviMRF/cmrf_core),
[CiviRemote & CiviRemote Events] (https://github.com/systopia/civiremote)
konzentrieren wird. Lass uns wissen, wenn Du daran interessiert bist,
teilzunehmen!

## Konfiguration/Verwendung

Wir beziehen uns hier sowohl auf die Haupterweiterung für das
Ressourcenmanagement als auch auf die "Ressourcen-CiviEvent-Integration". Für
die Konfiguration / Verwendung der anderen oben genannten Erweiterungen sollte
man sich auf die jeweilige Dokumentation beziehen. Nach der Installation der
Haupterweiterung ist keine weitere Konfiguration erforderlich. Für den Fall,
dass die "Ressourcen-CiviEvent-Integration" genutzt wird, finden scih im
Folgenden weitere Informationen zur Konfiguration und Verwendung.

### Kontakte als Ressourcen verfügbar machen

Zunächst muss man die gewünschten Kontakte als (menschliche) Ressourcen
verfügbar machen. Man kann dies für einen einzelnen Kontakt tun, indem man zum
Reiter "Ressourcenzuweisung" navigiert, auf "Ressource erstellen" klickt und
eine Ressourcenbezeichnung sowie den Ressourcentyp angibt. Man kann dies auch
mit der Massenaktion "Als Ressource verfügbar machen" aus einem beliebigen
Suchergebnis heraus tun.

### RessourcenBedarfe definieren und verwalten

In der Konfigurationsoberfläche jedes CiviCRM-Events, findet sich nun ein neuer
Reiter "Ressourcen". Derzeit ist dies der einzige Ort, an dem man
Ressourcenbedarfe definieren kann. Beim Hinzufügen eines Bedarfs, wählt man
seinen Typ und Bezeichnung sowie die Anzahl der benötigten Ressourcen.
Nach dem Hinzufügen eines Bedarfs ist es in aller Regel ratsam, eine Bedingung
zu erstellen, indem man*** auf "Ändern" in der Spalte "Bedingungen" klicken.
Bedingungen zur Verfügbarkeit legen den Zeitraum fest, in der die Ressource(n)
benötigt werden. Diese kann absolut oder relativ zum Start- und Enddatum des
Ereignisses sein. Vorsicht - wird keine Bedingung zur Verfügbarkeit angeben,
werden zugewiesene Ressourcen auf unbestimmte Zeit geblockt und stehen nicht für
andere Bedarfe zur Verfügung!
Man kann auch andere Bedingungen hinzufügen, die erfüllt sein müssen, um
Ressourcen zuzuweisen/zu matchen, z.B. dass die Kontakte einer bestimmten Gruppe
angehören oder ein bestimmtes Tag haben müssen.

### Einschränkungen der Ressourcenverfügbarkeit

Einem Bedarf zugewiesene Ressourcen sind nicht für sich zeitlich überschneidende
Bedarfe verfügbar bzw. werden nicht für diese vorgeschlagen. Darüber hinaus
können für jede Ressource allgemeine Verfügbarkeitsbeschränkungen (z. B. Urlaub
/ sonstige Abwesenheit) im Reiter Ressourcenzuweisungen angegeben werden. Diese
allgemeinen Beschränkungen verhindern ebenfalls, dass die Ressource für andere
Bedarfe während dieser Zeitspanne(n) vorgeschlagen wird.

### Abgleich & Verwaltung von Ressourcen für einen Bedarf

In der Konfigurationsoberfläche der Bedarfe können Ressourcen gesucht un
zugeordnet werden, die den konfigurierten Bedingungen entsprechen. Dafür klickt
man auf "Zuweisen" in der Spalte "Aktionen" und erhält dann eine Liste der
passenden Ressourcen (falls vorhanden). Aus dieser können bestimmte oder alle
Ressourcen ausgewählt und dem Bedarf zugeordnet werden.
In den Spalten "zugewiesen" und "erfüllt" wird die Anzahl aller Ressourcen
angezeigt, die zugewiesen sind und alle aktuell definierten Bedingungen
erfüllen. Wenn man auf eine Zahl in der Spalte "zugewiesen" klickt, wird eine
Liste der aktuell zugewiesenen Ressourcen angezeigt und die Zuweisung kann bei
Bedarf aufgehoben werden.

### Suche nach passenden Bedarfe für Ressourcen

Im Reiter "Ressourcenzuweisungen" einer Ressource kann man durch Klicken auf
das "+" im Bereich "Zuweisungen" nach Bedarfen suchen, deren Bedingungen von den
Ressourcen erfüllt werden. Aus der Liste ordnet man dann eine Ressource dem
gewünschten Bedarf zu. Im selben reiter kann man die Zuweisung einer Ressource
auch aufheben.

### Ressourcen-CiviEvent-Integration

Wie oben beschrieben, baut diese Erweiterung auf der Hauperweiterung für das
Ressourcenmanagement auf. Nach der Installation der Erweiterung navigiert man zu
deren Einstellungsseite (/civicrm/admin/setting/resourceevent?reset=1) und
definiert den positiven und negativen Status, der von der Erweiterung bei der
Erstellung/Aktualisierung eines Teilnehmerobjekts (Eventanmeldung) verwendet
werden soll. Bei der Installation wird eine spezielle Teilnehmerrolle namens "
Human Resource"  erstellt, die beim manuellen Erstellen oder Bearbeiten einer
Anmeldung über die Benutzeroberfläche nicht genutzt werden kann. Die Erweiterung
wird automatisch Eventanmeldungen für Ressourcenzuweisungen erstellen
synchronisieren:

- Wenn eine Ressource einem Bedarf zugewiesen wird, wird eine ggf. bestehende
  Anmeldung mit der Rolle "Human Resource" aktualisiert, andernfalls wird eine
  neue Anemldung erstellt.
- Wenn man die Zuordnung einer Ressource zu einem Bedarf aufhebt, wird die
  verknüpfte Anmeldung auf den von konfigurierten Teilnehmerstatus mit einer
  negativen Klasse aktualisiert.
- Wird eine Anmeldung mit positivem Status, der Rolle "Human Resource" und einem
  verknüpfteb Bedarf angelegt wird eine entsprechende Ressourcenzuweisung
  erstellt. Dies ist derzeit nicht über die Benutzeroberfläche möglich ist,
  sondern nur über bestimmte Erweiterungen (z.B. "Event Invitation") oder die
  API.
- Beim Löschen oder Änderung einer Anmeldung mit der Rolle "Human Resource" zu
  einem negativen Status wird auch eine damit verbundene Zuweisung gelöscht.
  Möglicherweise wird zukünftig ein komplexeres "Status-Synchronisations-Modell"
  implementiert.

# Game of Thrones Time Capsule

Bei diesem Projekt geht es um die Vorhersage,
wer bei Game of Thrones den Nachtkönig töten wird. Gerne darf man die Vorhersage ausschmücken, z.B. auf welche Art er getötet wird oder in welcher Situation.

Ich gehe einfach mal davon aus, dass dies mehr oder weniger
am Ende der letzten Staffel passieren wird.

Jeder darf eine Vorhersage machen und diese wird signiert und
verschlüsselt. Wenn dann der Moment gekommen ist,
öffnen wir alle Vorhersagen und wer am nächsten an der Lösung
dran ist, darf sich freuen. Einen Preis gibt es nicht.

# Mitmachen

1. eine Datei mit der Lösung erstellen. Da jeder User eine
   Datei committen wird, wird die Datei nach dem User benannt,
    also bspw. ``aabeling.txt``.
2. die Datei wird mit ``gpg`` signiert:

     $ gpg --output aabeling.txt.sig  --clearsign aabeling.txt
3. die signierte Datei wird verschlüsselt, sodass nur der Ersteller sie entschlüsseln kann:

     $ gpg -r achimabeling@web.de --encrypt --armor aabeling.txt.sig

   Dadurch wird die Datei ``aabeling.txt.sig.asc`` erzeugt.
4. ``aabeling.txt.sig.asc`` wird committed. Zu diesem Zeitpunkt kann nur der Ersteller sie lesen. Eine Verifikation der Signatur ist nicht möglich.
5. wenn die Entscheidung dann gefallen ist, kann jeder User seine Datei entschlüsseln und die entschlüsselte Datei committen. Dann kann auch jeder prüfen, ob die Signatur in Ordnung ist und ob die Datei wirklich vor der Entscheidung erstellt wurde.

Wer will kann sich auch das Committen der verschlüsselten Datei sparen und einfach die signierte Datei committen, nachdem die Entscheidung gefallen ist.

# Beispiel

     $ gpg --output aabeling.txt.sig --clearsign  aabeling.txt
     $ gpg -r achimabeling@web.de --encrypt --armor aabeling.txt.sig
     $ cat aabeling.txt.sig.asc

``aabeling.txt.sig.asc`` committen und abwarten.

     $ gpg aabeling.txt.sig.asc

``aabeling.txt.sig`` committen. Jeder kann dann mit

     $ gpg --verify aabeling.txt.sig

überprüfen, ob die Datei vor der Entscheidung signiert wurde.

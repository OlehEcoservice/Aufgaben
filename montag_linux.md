--Tagesziel 16.09--
-Mich mit Linux und Terminal kennenlernen
-Git und Versionierung durchmachen
-Kurs Lager weitermachen

--Grundlegende Linux-Befehle--
pwd -- wo ich gerade bin
ls -- was ist im Ordner (ls -l --Detailansicht | ls -la -- Versteckene Dateien | ls -lah -- alles+Dateiengrößen)
cd -- wechseln wo ich bin(cd ~ -- /home/user dabei | cd (ohne/) -- weiter gehen von geöffneten Ordner | cd / --alles /home/user...)
mkdir (Ordnername) -- erstellt einen Ordner
cp -- macht Copy (cp -r --für Ordner)
mv -- wechseln wo ist File oder umbennenen
rm -- delete (rm -r -- Delete Ordner)
cat -- sehen was ist im File drin
less -- öffnen das File im Terminal(q-exit | v-in Editor | )
head -- zeigt erste 10 Zeilen(-n -- nummer der Zeilen | -c n -- erste n Bytes der Datei)
tail -- alternativ zum head
ls -l | head -- zeigt erste 10 Files
grep -- Such (-rl -- enthalten)
find -- Such (-name | -iname | -name *.md | /tmp -mtime -n -- letzten n geändert | /etc -size +nM -- mehr als n Megabytes)


Task 4
ps aux | grep odoo
Resultat
user       33531  0.0  0.0   9552  2444 pts/1    S+   15:03   0:00 grep --color=auto odoo

Nach diesem Befehl habe ich festgestellt, dass es kein odoo.log gibt
ser@user-TP-Gen-4:~$ find /opt/odoo -name *.log
user@user-TP-Gen-4:~$ find /opt/odoo -name *.log 2>/dev/null
Ergebnis: kein
user@user-TP-Gen-4:~$ grep "logfile" /opt/odoo/19.0/customer/odoo19/odoo.cfg
; logfile wird über Daemon gesetzt
logfile = None

Aber es ist weil statt log File hier Teminal aufgeschrieben ist
aus dem Terminal:
Eine von der Startmeldung mit Typ INFO(server start):
2026-09-16 13:58:37,289 42200 INFO ? odoo.service.server: HTTP service (werkzeug) running on user-TP-Gen-4:19069 

eine von der Warnung mit Typ WARNUNG(Configuration):
2026-09-16 13:58:36,629 42200 WARNING ? odoo.tools.config: option addons_path, invalid addons directory '/opt/odoo/19.0/addons/oca/hr-expense', skipped 
Lösungsansatz:
Im Terminal prüfen, ob das Verzeichnis existiert:
ls -l /opt/odoo/19.0/addons/oca/hr-expense
Falls der Ordner fehlt, den Pfad in der odoo.cfg unter addons_path entfernen oder den fehlenden Ordner/das Git-Repository an dieser Stelle wiederherstellen.

Fehler: gibt es keine
--------------------------------------------


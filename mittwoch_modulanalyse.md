- Der Verzeichnisbaum von den wichtigsten Dateien des Modules "Project_task_product":
models
views
manifest.py
tests
--------------------------------------------
Beschreibung des Geschäftsprozess des Moduls:
manifest.py dient als die Registrierungskarte, Anmeldung und Konfiguration für das Modul: da steht kurz wichtige Information, was Modul braucht um zu funktionieren(Voraussetzungen) und welche UI Dateien geladen werden müssen. Das Modul benutzt Ordner Models - um die Funktion des Modul umzusetzen (logic) , und views um das Modul zu visualisieren. Tests Ordner dienen als Überprüfung, ob alles reibunglos läuft. In Static Ordner befindet sich alle statische Dateien - Bilder, CSS, JavaScrip, Web-Komponente. Das Modul arbeitet verknüpfend zusammen, um die eigene Aufgaben zu erledigen, dadurch braucht es Materialien von anderen Ordner oder Files.


- Die Abhängigkeiten in __manifest__.py:
modul "Project"
modul "Product"

- Geladene Dateien in __manifest__.py:
views/project_task_views.xml
views/product_views.xml

--------------------------------------------
- Für die Folgung des Python-Feld wähle ich 'product_id'. Das Feld 'product_id' ermöglicht die Verknüpfung einer Aufgabe     
    mit einem Produkt. Der Pfad ist:

1. Definition im Python-Modell ('models/project_task.py'):
   Das Feld wird im Modell 'project.task' definiert und legt den Bezug zum Produktmodell 'product.product' fest:
   'product_id = fields.Many2one(comodel_name="product.product", string="Product")'

2. Registrierung im Manifest ('manifest.py'):
   Das Manifest sorgt dafür, dass die entsprechende XML-Ansicht beim Installieren oder Aktualisieren geladen wird:
   '"data": ["views/project_task_views.xml", ...]'

3. Darstellung in der XML-Ansicht ('views/project_task_views.xml'):
   Das Feld wird an der gewünschten Stelle auf der Benutzeroberfläche gestellt:
   ' field name="product_id" '

#Webserver-Image

---

# Inhalt
- [Auftrag](#auftrag)
- [Anleitung und Erklärung](#anleitung-und-erklaerung)

---
# Auftrag

>1. Erstellen Sie ein eigenes Webserver-Image auf Basis eines geeigneten Images (z.B. node.js express, apache, nginx, php, ..) und lassen Sie darin eine einfache (statische) Webseite laufen (Sie können zum Beispiel die Webseite aus Modul 293 verwenden).
>    Die Webseite soll Bestandteil des Images sein und auf dem Host im Browser unter Port 8080 erreichbar sein.
>3. Starten Sie den Container am Ende so, dass sich die Dateien zur Webseite (HTML, CSS, etc.) und die Logdateien in lokalen Verzeichnissen befinden, damit die Webseite von dort aus weiterentwickelt werden kann.
>4. Dokumentieren Sie Ihr Mini-Projekt auf Github/Gitlab sinnvoll (inkl. Dockerfile) und geben Sie die URL dazu der Lehrperson ab.

---
# Anleitung  und Erklärung

Zuerst erstelle ich mir ein File für mein Mini-Projekt
````
mkdir mini-project
cd mini-project
````

In diesem File erstlle ich mir meinen Dockerfile und konfiguriere sie wie ich es brauche. Dabei ist zu beachten, dass ich php verwenden will. Dazu muss ich den Dockerfile ersterllen und danach bearbeiten.  In diese Dockerfile wurden einige Sachen definiert, wie zum Beispiel den Port, verzeichnis, usw.

cmd:

````
touch Dockerfile
nano Dockerfile
````

Dockerfile:

````
FROM php:8-apache
COPY index.php /var/www/html
````

Da wird nun in unserem Dockerfile das nötige für den Webserver definiert haben können wir nun in unserem verzeichnis unser index.php file hochladen.

index.php:

````
<!DOCTYPE html>
<html>
<head>
  <title>Meine Webseite</title>
  <style>
    /* Hier kommt der CSS-Code für das Styling der Webseite */
    body {
      font-family: Arial, sans-serif;
      margin: 0;
      padding: 0;
    }

    header {
      background-color: #333;
      color: #fff;
      padding: 20px;
    }

    main {
      padding: 20px;
    }

    footer {
      background-color: #333;
      color: #fff;
      padding: 20px;
    }
  </style>
</head>
<body>
  <header>
    <h1>Willkommen auf meiner Webseite</h1>
    <p>Hier finden Sie Informationen zu verschiedenen Themen.</p>
  </header>

  <main>
    <h2>Über uns</h2>
    <p>Wir sind ein Team von Experten, das Ihnen die neuesten Informationen und Ressourcen zu den interessantesten Themen zur Verfügung stellt.</p>

    <h2>Unsere Dienstleistungen</h2>
    <ul>
      <li>Webdesign und Entwicklung</li>
      <li>Content-Erstellung und -Optimierung</li>
      <li>Suchmaschinenoptimierung</li>
      <li>Social-Media-Marketing</li>
      <li>Online-Werbekampagnen</li>
    </ul>

    <h2>Unsere Mission</h2>
    <p>Unsere Mission ist es, Unternehmen und Einzelpersonen dabei zu helfen, ihre Online-Präsenz zu verbessern und ihre Ziele im digitalen Raum zu erreichen. Wir glauben an die Kraft des Internets und sind leidenschaftlich daran interessiert, unseren Kunden dabei zu helfen, erfolgreich zu sein.</p>
  </main>

  <footer>
    <p>&copy; 2023 Meine Webseite. Alle Rechte vorbehalten.</p>
  </footer>
</body>
</html>

````

Nach diesem Prozess erstellen wir nun unser Docker Image für den Webserver und benennen den Image ein-webserver.

````
docker build -t mein-webserver .
````

Nun müssen wir nur noch unser Container zum laufen bringen. 

````
docker run -d --name mein-webserver-container -p 8080:80 mein-webserver
````

Der Parameter "-p 8080:8080" verbindet den Host-Port 8080 mit dem Container-Port 8080, so dass die Webseite im Browser unter Port 8080 erreichbar ist. In diesem Fall können wir unser Webserver unter dem URL "localhost:8080" erreichen.

---

Nach diesem Tutorial solltest du dein Webserver haben.

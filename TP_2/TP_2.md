# TP - 2 Linux #



On va sur la vm Wiki, et nous allons crée un Virtual Host.

Pour cela nous commençons par nous rendre dans les site-availabes de apache 2 et nous crée le site "test"

```
sudo nano /etc/apache2/sites-available/test
```

Ensuite nous remplisions le ficher avec les informations qu'il faut 

```
<VirtualHost *:80>
	DocumentRoot /var/www/test
	ServerName   test.test
	ServerAlias  www.test.test
</VirtualHost>

```

( Il faut renomer le fichier test.test.conf sinon il sera imposible de lancer le site ) 

Un fois chose faite il faut aller crée le fichier test dans var/www.
Puis lancer la commande a2ensite test :

```
vagrant@wiki:~$ sudo a2ensite test.test.conf
Enabling site test.test.
To activate the new configuration, you need to run:
  systemctl reload apache2
```
Nous redémarons le system Apache et le serveur est accecible depuis la vm Wiki il faudras alors faire un telnet en directions de la vm wiki.
Une fois que nous en avons la possibilité nous rentrons GET / HTTP/1.0 affin de récupéré le contenus de la page.

```
vagrant@backup:~$ telnet test.test 80
Trying 23.217.138.108...
Connected to test.test.
Escape character is '^]'.
GET / HTTP/ 1
```

Le contenus de la page est ensuite afficher :
```
<body>
<p> cc </p>
</body>
```
Le gros soucis c'est que je n'arrive pas à initié cela dans le vagrant-file.

#[Kickstart WP](https://github.com/iacopolea/kickstart-wp)

KickStart WP vuole essere uno strumento per iniziare velocemente a sviluppare un sito web con Worpress in modo professionale.
È basato su [Bedrock](https://roots.io/bedrock/) e # [Sage](https://roots.io/sage/).
È importante leggere bene la documentazione riguardo questi due package.
Su github sono [https://github.com/roots/bedrock.git](https://github.com/roots/bedrock.git), e [https://github.com/roots/sage](https://github.com/roots/sage).


##Uso di questo strumento
Ci sono alcuni passi da eseguire.
Settare un buon ambiente di lavoro è complicato all'inizio ma da soddisfazione e permette di velocizzare il proprio workflow quando si eseguono sempre le stesse operazioni.

###DATABASE
In questo esempio ho settato un web server con php e mysql sul mio computer (una ottima guida [qui](http://jason.pureconcepts.net/2014/11/install-apache-php-mysql-mac-os-x-yosemite/)) e ho impostato i [virtualhost](http://jason.pureconcepts.net/2014/11/configure-apache-virtualhost-mac-os-x/).
Usciti vivi da questo passaggio non ci resta che:

1 - Creare un nuovo database su [http://localhost/phpmyadmin](http://localhost/phpmyadmin)
2 - Aprire un terminale, passare a root e editare un paio di file

```sh
sudo su -
vi /etc/apache2/vhosts/NOME-DEL-SITO.conf
```
aggiungere questa configurazione: (cambiare con la propria struttura di cartelle!)

```sh
<VirtualHost *:80>
        DocumentRoot "/Users/Iacopo/Sites/NOME-DEL-SITO/site/web/"
        ServerName NOME-DEL-SITO.local
        ErrorLog "/private/var/log/apache2/NOME-DEL-SITO.local-error_log"
        CustomLog "/private/var/log/apache2/NOME-DEL-SITO.local-access_log" common

        <Directory "/Users/Iacopo/Sites/NOME-DEL-SITO/site/web/">
            AllowOverride All
            Require all granted
        </Directory>
</VirtualHost>
```
Salvare, chiudere e ciao.
Per accedere a NOME-DEL-SITO.local devi editare l'hosts file

```sh
vi /etc/hosts
```
e aggiungere:
```sh
127.0.0.1       NOME-DEL-SITO.local
```

3 - Ok riavvia Apache e pulisci la cache dei DNS
```sh
apachectl restart
dscacheutil -flushcache
```

###Installazione di Kickstart Wp
Per quanto sia una vera rottura, dobbiamo essere sicuri di aver installato tutti i pacchetti e le dipendenze di Bedrock e Sage,
tipo Composer, Node.js, npm, Bower, wp-cli, e dio sa solo cos'altro (e rispettive documentazioni hanno info al riguardo, giuro).

4 - Possiamo procedere clonando la repo di kickstart-wp.
Ci posizioniamo nella cartella del sito e la copiamo dentro e tolgo il .git

```sh
git clone https://github.com/iacopolea/kickstart-wp . && rm -rf .git
```
Rinomino la cartella con un più generico `site`.

5 - Ora settiamo il file .env a partire dal template inserendo le info del database "appena" creato.

```sh
wp dotenv init --file=.env --with-salts --template=.env.example
```
usare `wp dotenv salts regenerate` se c'erano già le chiavi

6 - Avvio composer che mi installa le dipendenze
NB ho aggiunto ACF come plugin di default perchè lo uso spesso (è da attivare nella sezione plugin).
Nella cartella site eseguire composer e pregare che vada tutto bene.

```sh
composer install
```
Ok ci ha installato wp e siamo contenti, e adesso?

```sh

```
```sh

```
```sh

```
```sh

```




<h1>
    Istruzioni installazione Debian</h1>
<h2>
    Programmi da installare direttamente</h2>
<p>
    Deselezionare tutto a parte il server ssh e la configurazione standard (ultima riga). Non installare ambiente grafico!!!!</p>
<p>
<h2>
    Aggiunta di sudo</h2>
<p>
    Login come root e dare:</p>
<div class="code">
    <code>$ apt-get install sudo </code></div>
<p>
    Aggiungere l&#39;utente pippo al gruppo sudo:</p>
<div class="code">
    <code># adduser pippo sudo </code></div>
<p>
    Dopo essere stati aggiunto ad un nuovo gruppo, l&#39;utente deve fare il logout e quindi di nuovo il login affinch&eacute; l&#39;impostazione del nuovo gruppo abbia effetto. I gruppi vengono assegnati agli utenti solamente al momento del login. Una della maggiori fonti di confusione viene proprio dal fatto che gli utenti si aggiungono ad un gruppo, ma poi non fanno il logout e di nuovo il login e poi hanno problemi perch&eacute; non sono ancora stati assegnati ad un gruppo. Si pu&ograve; controllare di quali gruppi si fa parte usando i comandi <tt>id</tt> o <tt>groups</tt>.</p>
<p>
    &nbsp;</p>
<h2>Modifica del file <em>/etc/apt/source.list</em></h2>
<p>Effetuare la modifica del file <em>/etc/apt/source.list</em> con il comando:</p>
<div class="code"><code>$ sudo nano /etc/apt/source.list </code></div>
<p>
    Alle righe attive, aggiungere i repo <em>contrib</em> e <em>non-free</em>, in modo che le righe attive passino da cos&igrave;:</p>
<div class="code">
    <code>deb http://ftp.it.debian.org/debian/ wheezy main </code></div>
<p>			a cos&igrave;:</p>
<div class="code">
    <code>deb http://ftp.it.debian.org/debian/ wheezy main contrib non-free </code></div>
<p> Eseguire il seguente comando per aggiornare le liste pacchetti:</p>
<div class="code">
    <code>sudo apt-get update</code></div>
<h2>
    Configurare l&#39;interfaccia di rete, se abbiamo bisogno di un ip statico:</h2>
<p>
    Per tale motivo modifichiamo il file <em>/etc/network/interfaces</em> tramite il comando:</p>
<div class="code">
    <code>$ sudo nano /etc/network/interfaces </code></div>
<p>
    e, posto che la nostra rete sia collegata ad un router con IP 192.168.0.1, rendiamolo simile al seguente:</p>
<div class="code">
    <code># This file describes the network interfaces available on your system<br />
        # and how to activate them. For more information, see interfaces(5).<br />
        # The loopback network interface<br />
        auto lo<br />
        iface lo inet loopback<br />
        # The primary network interface auto eth0<br />
        iface eth0 inet static<br />
        address 192.168.0.100<br />
        netmask 255.255.255.0<br />
        network 192.168.0.0<br />
        broadcast 192.168.0.255<br />
        gateway 192.168.0.1<br />
    </code></div>
<p>
    In questo caso, l&#39;interfaccia di rete utilizzata &egrave; eth0 e l&#39;IP assegnato &egrave; 192.168.0.100. Per conoscere le interfacce di rete presenti sulla propria macchina &egrave; possibile utilizzare il comando <tt>ifconfig</tt>, che fornir&agrave; un elenco di tutte quelle collegate ed attive. L&#39;IP pu&ograve; essere scelto a piacere, purch&eacute; sia del tipo 192.168.0.X, dove X &egrave; un numero compreso tra 2 e 254.</p>
<p>
    Andiamo adesso a modificare il file <em>/etc/hosts</em> per far s&igrave; che la macchina riconosca l&#39;indirizzo IP scelto:</p>
<div class="code">
    <code>$ sudo nano /etc/hosts </code></div>
<p>
    e aggiungiamo la riga</p>
<div class="code">
    <code>192.168.0.100 ubuntu </code></div>
<p>
    utilizzando lo stesso IP scelto prima, e dove <em>ubuntu</em> &egrave; il nome di host che abbiamo assegnato alla macchina durante la fase di installazione, reperibile anche tramite il comando</p>
<div class="code">
    <code>$ cat /etc/hostname </code></div>
<p>
    Passiamo alla configurazione dei server DNS, tramite la modifica del file <em>/etc/resolv.conf</em>:</p>
<div class="code">
    <code>$ sudo nano /etc/resolv.conf </code></div>
<p>
    Una scelta universale &egrave; quella di utilizzare il servizio gratuito offerto da OpenDNS, aggiungendo a tale file le seguenti righe:</p>
<div class="code">
    <code># OpenDNS<br />
        nameserver 208.67.220.220<br />
        nameserver 208.67.222.222 </code></div>
<p>
    Riavviamo la macchina tramite il comando</p>
<div class="code">
    <code>$ sudo reboot </code></div>
<p>
    e testiamo la connessione &ldquo;pingando&rdquo; un sito web a piacere, ad esempio</p>
<div class="code">
    <code>$ ping www.google.it </code></div>
<p>
    Nel caso in cui tutto sia stato configurato in maniera corretta, si ricever&agrave; una risposta ai pacchetti inviati tramite ping, segno che la connessione funziona, altrimenti &egrave; necessario riconfigurare i parametri di rete e correggere eventuali errori commessi.</p>
<p>
    &nbsp;</p>
<div class="code">
    <code>			
        address 192.168.1.52<br />
        netmask 255.255.255.0<br />
        gateway 192.168.1.21<br />
        dns-nameservers 8.8.4.4 8.8.8.8<br /></code></div>
<div class="code">
    <code>sudo apt-get install apache2</code></div>
<div class="code">
    <code>sudo apt-get install samba cifs-utils<br />
        [global]<br />
        workgroup = GRUPPODILAVORO<br />
        server string = DESCRIZIONE<br />
        allow hosts = 192.168.1.0/24<br />
        wins support = yes<br />
        security = share<br />
        share modes = yes<br />
        encrypt passwords = no<br />
        [nomecondivisione]<br />
        comment = commento_condivisione<br />
        path = /path/da/condividere/ESEMPIO<br />
        read only = no<br />
        guest ok = yes<br />
        guest only = yes<br />
        create mask = 0777<br />
        directory mask = 0777</code></div>
<h2>php8</h2>
<div class="code">
    <code>sudo apt update</code></div>
<div class="code">
    <code>sudo apt install -y lsb-release ca-certificates apt-transport-https software-properties-common gnupg2<br />
        <br />
echo "deb https://packages.sury.org/php/ $(lsb_release -sc) main" | sudo tee /etc/apt/sources.list.d/sury-php.list<br />
wget -qO - https://packages.sury.org/php/apt.gpg | sudo apt-key add -<br />
sudo apt update </code></div>
<div class="code">
    <code>sudo apt install php libapache2-mod-php php8.1-mysql php8.1-common php8.1-mysql php8.1-xml php8.1-xmlrpc php8.1-curl php8.1-gd php8.1-imagick php8.1-cli php8.1-dev php8.1-imap php8.1-mbstring php8.1-opcache php8.1-soap php8.1-zip php8.1-intl -y
installare php8.x</code></div>
sudo apt-get install -y composer
sudo apt install mariadb-server
sudo mysql_secure_installation 

curl -fsSL https://deb.nodesource.com/setup_lts.x | sudo bash -
sudo apt-get install -y nodejs
echo fs.inotify.max_user_watches=524288 | sudo tee -a /etc/sysctl.conf
sudo sysctl -p

wget -O composer-setup.php https://getcomposer.org/installer
sudo php composer-setup.php --install-dir=/usr/local/bin --filename=composer<br />
<br />
composer create-project laravel/laravel nomeapp<br />
mv env file to app directory<br />
cd ./nomeapp<br />
php artisan key:generate<br />
sudo chmod -R 777 ./storage/<br />
setting /app/config/app.php (name, debug_mode, locale, ecc)<br />
php artisan migrate<br />


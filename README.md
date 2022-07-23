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
		<h2>
			Modifica del file <em>/etc/apt/source.list</em></h2>
		<p>
			Effetuare la modifica del file <em>/etc/apt/source.list</em> con il comando:</p>
		<div class="code">
			<code>$ sudo nano /etc/apt/source.list </code></div>
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

<h1>
			Istruzioni</h1>
		<p>
			A partire da Debian 6.0 (Squeeze), la procedura di boot da dispositivo USB o SD card &egrave; stata ulteriormente semplificata. Questo consentir&agrave;, a chi volesse installare Debian, di impartire un unico comando per la creazione di un dispositivo (USB o SD card) bootabile.</p>
		<p>
			&Egrave; sufficiente scaricare un&#39;immagine .iso (primo CD/DVD, netinst o mini.iso, vedi la guida Installare Debian), accertarsi che il dispositivo non sia montato e che la sua capacit&agrave; sia tale da contenere l&#39;immagine. Quindi basta un:</p>
		<div class="code">
			<code># dd if=/percorso/nome_immagine.iso of=/dev/sdb bs=4M; sync </code></div>
		<p>
			e ritrovarsi una pendrive USB o una scheda SD bootabile per installare Debian.</p>
		<div class="code warning">
			<b>ATTENZIONE</b><br />
			Il precedente esempio riguarda una pendrive riconosciuta come &quot;sdb&quot;. Accertatevi di inserire il device corretto poich&eacute; il precedente comando cancella ogni dato presente sul dispositivo.<br />
			<p>
				Utilizzare il comando:</p>
			<div class="code">
				<code># fdisk -l </code></div>
			<p>
				per dissipare eventuali dubbi.</p>
		</div>

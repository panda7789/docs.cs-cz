### <a name="throttle-concurrent-requests-per-session"></a>Omezení souběžných požadavků na relaci

|   |   |
|---|---|
|Podrobnosti|V rozhraní .NET Framework 4.6.2 a starší, ASP.NET provede žádosti s identifikátorem Sessionid stejné postupně a ASP.NET vždy problémy Sessionid pomocí souborů cookie ve výchozím nastavení. Pokud na stránce trvá dlouhou dobu reagovat, ji budou výrazně snížit výkon serveru právě stisknutím klávesy F5 v prohlížeči. V opravu jsme přidali čítače na sledování zařazených do fronty požadavků a ukončení požadavky po překročení zadané omezení. Výchozí hodnota je 50. Pokud bude dosažen limit, bude protokolována upozornění v případě, že protokol a odpovědi HTTP 500 mohou být zaznamenány v protokolu služby IIS.|
|Návrh|Pokud chcete obnovit původní chování, můžete přidat následující nastavení do souboru web.config pro vyjádření výslovného nesouhlasu nové chování.<pre><code class="language-xml">&lt;appSettings&gt;&#13;&#10;&lt;add key=&quot;aspnet:RequestQueueLimitPerSession&quot; value=&quot;2147483647&quot;/&gt;&#13;&#10;&lt;/appSettings&gt;&#13;&#10;</code></pre>|
|Rozsah|Edge|
|Version|4.7|
|Typ|Změna orientace|


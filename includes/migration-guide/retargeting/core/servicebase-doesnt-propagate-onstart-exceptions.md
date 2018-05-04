### <a name="servicebase-doesnt-propagate-onstart-exceptions"></a>ServiceBase není rozšířit OnStart výjimky

|   |   |
|---|---|
|Podrobnosti|V rozhraní .NET Framework 4.7 a dřívějších verzí, výjimek vyvolaných na spuštění služby nebudou rozšířeny do volajícího <xref:System.ServiceProcess.ServiceBase.Run%2A?displayProperty=nameWithType>.<br/>Počínaje aplikací, které cílí na rozhraní .NET Framework 4.7.1, modul runtime rozšíří výjimky <xref:System.ServiceProcess.ServiceBase.Run%2A?displayProperty=nameWithType> pro služby, které se nepodařilo spustit.|
|Návrh|Při spuštění služby pokud dojde k výjimce této výjimky se rozšíří. To by měly pomoci diagnostikovat případech, kde nepodaří se spustit službu. <br/>Pokud je toto chování žádoucí, se můžete rozhodnout mimo ho přidáním následující <AppContextSwitchOverrides> elementu, který chcete <runtime> oddíl konfiguračního souboru aplikace:<pre><code class="lang-xml">&lt;AppContextSwitchOverrides value=&quot;Switch.System.ServiceProcess.DontThrowExceptionsOnStart=true&quot; /&gt;&#13;&#10;</code></pre>Pokud aplikace cílí starší verze než 4.7.1, ale budete chtít mít toto chování, přidejte následující <AppContextSwitchOverrides> elementu, který chcete <runtime> oddíl konfiguračního souboru aplikace:<pre><code class="lang-xml">&lt;AppContextSwitchOverrides value=&quot;Switch.System.ServiceProcess.DontThrowExceptionsOnStart=false&quot; /&gt;&#13;&#10;</code></pre>|
|Rozsah|Vedlejší|
|Version|4.7.1|
|Typ|Změna orientace|
|Ovlivněné rozhraní API|<ul><li><xref:System.ServiceProcess.ServiceBase.Run(System.ServiceProcess.ServiceBase)?displayProperty=nameWithType></li><li><xref:System.ServiceProcess.ServiceBase.Run(System.ServiceProcess.ServiceBase[])?displayProperty=nameWithType></li></ul>|


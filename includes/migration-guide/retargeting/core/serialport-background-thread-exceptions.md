### <a name="serialport-background-thread-exceptions"></a>Portu SerialPort pozadí vlákno výjimky

|   |   |
|---|---|
|Podrobnosti|Vytvořena s vlákna na pozadí <xref:System.IO.Ports.SerialPort> datové proudy už ukončení procesu, když nastanou výjimky operačního systému. V aplikacích, které cílí na rozhraní .NET Framework 4.7 a starší verze, proces, je ukončen po je vyvolána výjimka operačního systému na vlákna na pozadí vytvořené pomocí <xref:System.IO.Ports.SerialPort> datového proudu. V aplikacích, cílové rozhraní .NET Framework 4.7.1 nebo novější verzi vlákna na pozadí počkejte OS události související s active sériového portu a může dojít k chybě v některých případech, například nečekané odebrání sériového portu.|
|Návrh|Pro aplikace, které cílí na rozhraní .NET Framework 4.7.1, můžete zamítnutí zpracování výjimek, pokud není žádoucí přidáním následujícího <code>&lt;runtime&gt;</code> část vaší <code>app.config</code> souboru:<pre><code class="language-xml">&lt;runtime&gt;&#13;&#10;&lt;AppContextSwitchOverrides value=&quot;Switch.System.IO.Ports.DoNotCatchSerialStreamThreadExceptions=true&quot; /&gt;&#13;&#10;&lt;/runtime&gt;&#13;&#10;</code></pre>Pro aplikace, které cílí na starší verze rozhraní .NET Framework, ale spustit v rozhraní .NET Framework 4.7.1 nebo novější, můžete se rozhodnout v zpracování přidáním následujícího výjimek <code>&lt;runtime&gt;</code> část vaší <code>app.config</code> souboru:<pre><code class="language-xml">&lt;runtime&gt;&#13;&#10;&lt;AppContextSwitchOverrides value=&quot;Switch.System.IO.Ports.DoNotCatchSerialStreamThreadExceptions=false&quot; /&gt;&#13;&#10;&lt;/runtime&gt;&#13;&#10;</code></pre>|
|Rozsah|Vedlejší|
|Version|4.7.1|
|Typ|Změna orientace|
|Ovlivněné rozhraní API|<ul><li><xref:System.IO.Ports.SerialPort?displayProperty=nameWithType></li></ul>|


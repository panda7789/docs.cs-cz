### <a name="winrt-stream-adapters-no-long-call-flushasync-automatically-on-close"></a>WinRT datového proudu adaptéry žádné dlouhé volání FlushAsync automaticky při zavření

|   |   |
|---|---|
|Podrobnosti|V aplikacích pro Windows Store prostředí Windows Runtime datového proudu adaptéry už volat metodu FlushAsync z metodu Dispose.|
|Návrh|Tato změna by měla být průhledná. Vývojáři obnovit předchozí chování psaní kódu takto:<pre><code class="lang-csharp">using (var stream = GetWindowsRuntimeStream() as Stream)&#13;&#10;{&#13;&#10;// do something&#13;&#10;await stream.FlushAsync();&#13;&#10;}&#13;&#10;</code></pre>|
|Rozsah|Transparentní|
|Version|4.5.1|
|Typ|Modul runtime|


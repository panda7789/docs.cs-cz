### <a name="wpf-dispatchersynchronizationcontextcreatecopy-now-returns-a-new-copy-instead-of-the-current-instance"></a>WPF DispatcherSynchronizationContext.CreateCopy nyní vrátí novou kopii místo aktuální instance

|   |   |
|---|---|
|Podrobnosti|V rozhraní .NET Framework 4 <xref:System.Windows.Threading.DispatcherSynchronizationContext.CreateCopy> vrátí odkaz na aktuální instanci, především jako optimalizace výkonu. V rozhraní .NET Framework 4.5 vrátí novou instanci, která vám umožní poprvé k závěru, že stejné odkazy indikovat, že provádění vlákna kontext synchronizace správné.  Není pravděpodobné, že bude mít vliv kód, který ověří identitu tyto odkazy, ale z důvodu změny, kód, který volá <xref:System.Windows.Threading.DispatcherSynchronizationContext.CreateCopy> by měl být testována jako součást migrace na rozhraní .NET Framework 4.5 nebo novější.|
|Návrh|Mějte na paměti, <xref:System.Windows.Threading.DispatcherSynchronizationContext.CreateCopy> nyní vrátí novou <xref:System.Threading.SynchronizationContext?displayProperty=name> objektu. Kód, který používá ekvivalenční odkazy generované tímto způsobem dříve, nebyla ve skutečnosti kontroluje, zda byla v kontextu správné, ale nemá při postavené na rozhraní .NET Framework 4.5 nebo novější.  Při pravděpodobně způsobit problémy, výkonu cesty ovlivněných kódu by vám měly dostatečně k určení, pokud to ale představuje jakýkoli problém.|
|Rozsah|Vedlejší|
|Version|4.5|
|Typ|modul runtime|
|Ovlivněné rozhraní API|<ul><li><xref:System.Windows.Threading.DispatcherSynchronizationContext.CreateCopy?displayProperty=nameWithType></li></ul>|


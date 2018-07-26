### <a name="change-in-behavior-for-taskwaitall-methods-with-time-out-arguments"></a>Změna chování pro metody Task.WaitAll s argumenty časového limitu

|   |   |
|---|---|
|Podrobnosti|<xref:System.Threading.Tasks.Task.WaitAll%2A?displayProperty=nameWithType> chování byla provedena konzistentnější v rozhraní .NET Framework 4.5.In rozhraní .NET Framework 4, tyto metody chovaly nekonzistentně. Po vypršení časového limitu, pokud jeden nebo více úlohy nebyly dokončeny nebo došlo ke zrušení před voláním metody, vyvolala metoda výjimku <xref:System.AggregateException?displayProperty=name> výjimky. Pokud časový limit vypršel, když žádné úlohy nebyly dokončeny nebo došlo ke zrušení před voláním metody, ale jeden nebo více úloh zadalo tyto stavy po volání metody, metoda vrátila hodnotu false.<br/><br/>V rozhraní .NET Framework 4.5, tato přetížení metody nyní vrátí hodnotu false, pokud žádné úlohy jsou stále spuštěna, když uplynutím časového limitu, a generují výjimku <xref:System.AggregateException?displayProperty=name> výjimku pouze v případě, že vstupní úloha byla zrušena (bez ohledu na to, jestli byl před nebo po metodu volání) a jsou pořád spuštěné žádné úlohy.|
|Návrh|Pokud <xref:System.AggregateException?displayProperty=name> se zachycení jako způsob zjišťování úlohu, která byla zrušena před verzí <xref:System.Threading.Tasks.Task.WaitAll%2A> volání volaná kód by měl místo toho proveďte stejné zjišťování prostřednictvím <xref:System.Threading.Tasks.Task.IsCanceled%2A> vlastnosti (například:. Any(t =&gt; t.IsCanceled)) od rozhraní .NET Framework 4.6 pouze vyvolá v takovém případě všechny očekávané úlohy jsou dokončeny před časový limit.|
|Rozsah|Vedlejší|
|Version|4.5|
|Typ|Modul runtime|
|Ovlivněné rozhraní API|<ul><li><xref:System.Threading.Tasks.Task.WaitAll(System.Threading.Tasks.Task[],System.Int32)?displayProperty=nameWithType></li><li><xref:System.Threading.Tasks.Task.WaitAll(System.Threading.Tasks.Task[],System.Int32,System.Threading.CancellationToken)?displayProperty=nameWithType></li><li><xref:System.Threading.Tasks.Task.WaitAll(System.Threading.Tasks.Task[],System.TimeSpan)?displayProperty=nameWithType></li></ul>|


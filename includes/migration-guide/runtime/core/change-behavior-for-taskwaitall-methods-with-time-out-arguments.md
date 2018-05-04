### <a name="change-in-behavior-for-taskwaitall-methods-with-time-out-arguments"></a>Změna v chování pro metody Task.WaitAll s argumenty časový limit

|   |   |
|---|---|
|Podrobnosti|<xref:System.Threading.Tasks.Task.WaitAll%2A?displayProperty=nameWithType> chování byl proveden víc konzistentní v rozhraní .NET Framework 4.5.In rozhraní .NET Framework 4, tyto metody se choval nekonzistentně. Pokud vypršela platnost časový limit, pokud jeden nebo více úloh, byly dokončeny nebo zrušena před volání metody, metodu došlo <xref:System.AggregateException?displayProperty=name> výjimka. Pokud vypršela platnost časový limit, pokud žádné úlohy byly dokončeny nebo zrušena před volání metody, ale jeden nebo více úloh, zadat tyto stavy po volání metody, metodu vrátila hodnotu false.<br/><br/>V rozhraní .NET Framework 4.5, tato metoda přetížení teď vrátit hodnotu NEPRAVDA, pokud žádné úlohy jsou stále spuštěn, když vyprší časový limit a vyvolají <xref:System.AggregateException?displayProperty=name> výjimka pouze v případě, že vstupní úloha byla zrušena (bez ohledu na to, jestli byl před nebo po metodě volání) a jsou stále spuštěné žádné další úlohy.|
|Návrh|Pokud <xref:System.AggregateException?displayProperty=name> se zachycení jako způsob zjišťování úlohu, která byla zrušena před <xref:System.Threading.Tasks.Task.WaitAll%2A> volání volaná, že kód místo toho provádět stejné detekce prostřednictvím <xref:System.Threading.Tasks.Task.IsCanceled%2A> vlastnosti (například:. Any(t =&gt; t.IsCanceled)) vzhledem k tomu, že rozhraní .NET Framework 4.6 pouze vyvolá v takovém případě pokud awaited všechny úkoly dokončené před časový limit.|
|Rozsah|Vedlejší|
|Version|4.5|
|Typ|Modul runtime|
|Ovlivněné rozhraní API|<ul><li><xref:System.Threading.Tasks.Task.WaitAll(System.Threading.Tasks.Task[],System.Int32)?displayProperty=nameWithType></li><li><xref:System.Threading.Tasks.Task.WaitAll(System.Threading.Tasks.Task[],System.Int32,System.Threading.CancellationToken)?displayProperty=nameWithType></li><li><xref:System.Threading.Tasks.Task.WaitAll(System.Threading.Tasks.Task[],System.TimeSpan)?displayProperty=nameWithType></li></ul>|


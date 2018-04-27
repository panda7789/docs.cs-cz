### <a name="etw-event-names-cannot-differ-only-by-a-start-or-stop-suffix"></a>Názvy události trasování událostí pro Windows nejde liší pouze příponu "Start" nebo "Stop"

|   |   |
|---|---|
|Podrobnosti|V rozhraní .NET Framework 4.6 a 4.6.1, modul runtime vyvolá <xref:System.ArgumentException> při dva názvy události trasování událostí pro Windows (ETW) se liší pouze &quot;spustit&quot; nebo &quot;Zastavit&quot; přípony (jako když je jedna událost s názvem <code>LogUser</code>a druhou s názvem <code>LogUserStart</code>). V takovém případě modulu runtime nelze vytvořit zdroj události, který nelze emitování žádné protokolování.<ul><li>[X] quirked / / používá stejný mechanismus Chcete-li funkci zapnout nebo vypnout, obvykle pomocí cílení AppContext nebo konfigurační soubory modulu runtime. Musí být automaticky zapnout v některých situacích.</li><li>[] Sestavení času přerušení / / zalomení dojde, pokud se pokus o její kompilace</li></ul>|
|Návrh|Pokud chcete zabránit výjimku, ujistěte se, že žádné názvy dvou událostí se liší pouze &quot;spustit&quot; nebo &quot;Zastavit&quot; příponu. Tento požadavek se odebere od verze rozhraní .NET Framework 4.6.2; modul runtime můžete odstranit nejednoznačnost názvy událostí, které se liší pouze &quot;spustit&quot; a &quot;Zastavit&quot; příponu.|
|Rozsah|Edge|
|Version|4.6|
|Typ|Modul runtime|


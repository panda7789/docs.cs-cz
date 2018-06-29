### <a name="systemthreadingtaskstask-no-longer-throw-objectdisposedexception-after-object-is-disposed"></a>System.Threading.Tasks.Task už throw ObjectDisposedException po objekt je zveřejněn.

|   |   |
|---|---|
|Podrobnosti|S výjimkou <xref:System.Threading.Tasks.Task.System%23IAsyncResult%23AsyncWaitHandle>, <xref:System.Threading.Tasks.Task?displayProperty=name> metody už throw <xref:System.ObjectDisposedException?displayProperty=name> výjimka po uvolnění objektu. Tato změna podporuje použití úloh v mezipaměti. Například metoda může vrátit úlohu uloženou v mezipaměti pro zastupování již dokončené operace namísto přidělení nové úlohy. To nebylo v předchozích verzích rozhraní .NET Framework možné, protože příjemci úlohy s ní mohli nakládat.|
|Návrh|Uvědomte si, že metody úloh může už throw <xref:System.ObjectDisposedException?displayProperty=name> v případech, kdy je objekt zlikvidován. Pokud aplikace se v závislosti na výjimku vědět, že úloha byla zrušena, by měl aktualizovat explicitně zkontrolovat stav úkolu pomocí <xref:System.Threading.Tasks.Task.Status>.|
|Rozsah|Vedlejší|
|Version|4.5|
|Typ|modul runtime|


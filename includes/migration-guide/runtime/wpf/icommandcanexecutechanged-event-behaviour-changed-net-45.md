### <a name="icommandcanexecutechanged-event-behaviour-changed-in-net-45"></a>Chování událostí ICommand.CanExecuteChanged změnit v rozhraní .NET 4.5

|   |   |
|---|---|
|Podrobnosti|V rozhraní .NET Framework 4.5 <xref:System.Windows.Input.ICommand.CanExecuteChanged?displayProperty=name> byla ignorována, pokud byl objekt stejný jako objekt, který vyvolá událost odesílatel události. Tato chyba byla opravena v rozhraní .NET Framework 4.5 aktualizace údržby.|
|Návrh|Tato chyba byl opraven v rozhraní .NET Framework 4.5 obsluhy verze, takže se můžete vyhnout tím, že zajistí, že je aktuální rozhraní .NET Framework nebo upgrade na rozhraní .NET Framework 4.5.1. Alternativně kódu aplikace pomocí <xref:System.Windows.Input.ICommand?displayProperty=name> můžete upravit tak, aby Ujistěte se, že odesílatel při vyvolání <xref:System.Windows.Input.ICommand.CanExecuteChanged?displayProperty=name> příkaz je stejný jako objekt vyvolá událost.|
|Rozsah|Vedlejší|
|Version|4.5|
|Typ|Modul runtime|
|Ovlivněné rozhraní API|<ul><li><xref:System.Windows.Input.ICommand.CanExecuteChanged?displayProperty=nameWithType></li></ul>|
|Analyzátory|<ul><li>CD0084</li></ul>|


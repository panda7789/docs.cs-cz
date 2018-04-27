### <a name="appdomainsetupdynamicbase-is-no-longer-randomized-by-userandomizedstringhashalgorithm"></a>AppDomainSetup.DynamicBase už náhodně mění podle userandomizedstringhashalgorithm –

|   |   |
|---|---|
|Podrobnosti|Před rozhraní .NET Framework 4.6, hodnota <xref:System.AppDomainSetup.DynamicBase> by se náhodně mění, mezi doménami aplikací, nebo mezi procesy, pokud bylo userandomizedstringhashalgorithm – povolené v konfiguračním souboru aplikace. Od verze rozhraní .NET Framework 4.6 <xref:System.AppDomainSetup.DynamicBase> vrátí výsledku stabilní mezi různými instancemi spuštění aplikace a mezi doménami jinou aplikaci. Dynamické základů budou stále lišit pro různé aplikace; Tato změna pouze odebere náhodných pojmenování element pro různé instance stejné aplikaci.|
|Návrh|Uvědomte si, že povolení <code>UseRandomizedStringHashAlgorithm</code> nebude mít za následek <xref:System.AppDomainSetup.DynamicBase> se náhodně mění. V případě potřeby náhodných základní musí být vytvořeného v kódu aplikace a nikoli prostřednictvím toto rozhraní API.|
|Rozsah|Edge|
|Version|4.6|
|Typ|Modul runtime|
|Ovlivněné rozhraní API|<ul><li><xref:System.AppDomainSetup.DynamicBase?displayProperty=nameWithType></li></ul>|


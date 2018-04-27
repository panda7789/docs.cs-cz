### <a name="dataobjectgetdata-now-retrieves-data-as-utf-8"></a>DataObject.GetData nyní načítá data jako UTF-8

|   |   |
|---|---|
|Podrobnosti|Pro aplikace, která cílí na rozhraní .NET Framework 4 nebo které běží na rozhraní .NET Framework 4.5.1 nebo dřívějších verzí <code>DataObject.GetData</code> načte data ve formátu HTML jako řetězec ve formátu ASCII. V důsledku toho jiné znaky než ASCII (znaky jsou větší než 0x7F jejichž kódů ASCII) jsou reprezentované pomocí dvou náhodných znaků. Pro aplikace, které cílí na rozhraní .NET Framework 4.5 nebo novější a spustit v rozhraní .NET Framework 4.5.2 <code>DataObject.GetData</code> načte data ve formátu HTML jako znakové sady UTF-8, které představuje znaky, které jsou větší než 0x7F správně.|
|Návrh|Pokud jste implementovali řešení pro kódování problém s řetězce ve formátu HTML (například podle explicitně kódování HTML řetězec načíst ze schránky předáním jeho <xref:System.Text.UTF8Encoding.GetString(System.Byte[],System.Int32,System.Int32)?displayProperty=name>) a že změna orientace aplikace z verze 4 na 4.5, který alternativní řešení, měla by být odebrána. Pokud z nějakého důvodu není nutná staré chování, můžete vybrat aplikace rozhraní .NET Framework 4.0 tohoto chování.|
|Rozsah|Edge|
|Version|4.5.2|
|Typ|Změna orientace|
|Ovlivněné rozhraní API|<ul><li><xref:System.Windows.DataObject.GetData(System.String)?displayProperty=nameWithType></li><li><xref:System.Windows.DataObject.GetData(System.Type)?displayProperty=nameWithType></li><li><xref:System.Windows.DataObject.GetData(System.String,System.Boolean)?displayProperty=nameWithType></li></ul>|


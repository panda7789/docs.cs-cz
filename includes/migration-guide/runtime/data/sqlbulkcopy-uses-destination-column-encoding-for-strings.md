### <a name="sqlbulkcopy-uses-destination-column-encoding-for-strings"></a>SqlBulkCopy používá cílový sloupec kódování pro řetězce

|   |   |
|---|---|
|Podrobnosti|Při vkládání dat do sloupce, <xref:System.Data.SqlClient.SqlBulkCopy?displayProperty=name> používá kódování cílový sloupec než výchozí kódování pro <code>VARCHAR</code> a <code>CHAR</code> typy. Tato změna eliminuje možnost poškození dat při použití výchozího kódování, pokud cílový sloupec nepoužívá výchozí kódování. Ve výjimečných případech existující aplikaci throw výjimky SqlException Pokud změna v kódování vytvoří data, která je příliš velká a nevejde se do cílový sloupec.|
|Návrh|Který očekávat <xref:System.Data.SqlClient.SqlBulkCopy?displayProperty=name> už poškodí data kvůli překročení kódování rozdíly. Pokud řetězce blíží limitu velikosti cílový sloupec se kopírují, může být nutné buď předem zakódovat data (který se má zkopírovat zkontrolujte, že data se vejde cílový sloupec) nebo catch <xref:System.Data.SqlClient.SqlException?displayProperty=name>s.|
|Rozsah|Edge|
|Version|4.5|
|Typ|modul runtime|
|Ovlivněné rozhraní API|<ul><li><xref:System.Data.SqlClient.SqlBulkCopy?displayProperty=nameWithType></li><li><xref:System.Data.SqlClient.SqlBulkCopy.%23ctor(System.Data.SqlClient.SqlConnection)?displayProperty=nameWithType></li></ul>|


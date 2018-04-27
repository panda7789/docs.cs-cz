### <a name="objectcontexttranslate-and-objectcontextexecutestorequery-now-support-enum-type"></a>ObjectContext.Translate a ObjectContext.ExecuteStoreQuery teď podporují typ výčtu.

|   |   |
|---|---|
|Podrobnosti|V rozhraní .NET 4.0, obecný parametr <code>T</code> z <code>ObjectContext.Translate</code> a <code>ObjectContext.ExecuteStoreQuery</code> metody nelze výčtu. Tento scénář se teď podporuje.|
|Návrh|Pokud přeložit nebo ExecuteStoreQuery byla volána na typu výčtu v rozhraní .NET 4.0, byl vrácen '0'. Pokud toto chování žádoucí, měl by být volání nahrazen konstanta 0 (nebo ekvivalentní výčtu je).|
|Rozsah|Edge|
|Version|4.5|
|Typ|Modul runtime|
|Ovlivněné rozhraní API|<ul><li><xref:System.Data.Objects.ObjectContext.Translate%60%601(System.Data.Common.DbDataReader)?displayProperty=nameWithType></li><li><xref:System.Data.Objects.ObjectContext.Translate%60%601(System.Data.Common.DbDataReader,System.String,System.Data.Objects.MergeOption)?displayProperty=nameWithType></li><li><xref:System.Data.Objects.ObjectContext.ExecuteStoreQuery%60%601(System.String,System.Object[])?displayProperty=nameWithType></li><li><xref:System.Data.Objects.ObjectContext.ExecuteStoreQuery%60%601(System.String,System.String,System.Data.Objects.MergeOption,System.Object[])?displayProperty=nameWithType></li></ul>|


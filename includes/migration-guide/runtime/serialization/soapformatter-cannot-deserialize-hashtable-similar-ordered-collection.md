### <a name="soapformatter-cannot-deserialize-hashtable-and-similar-ordered-collection-objects"></a>SoapFormatter nelze deserializovat zatřiďovací tabulky a podobné seřazené kolekce objektů

|   |   |
|---|---|
|Podrobnosti|<xref:System.Runtime.Serialization.Formatters.Soap.SoapFormatter?displayProperty=name> Nemá není záruku, že objekty serializované do jedné verze rozhraní .NET Framework bude úspěšně deserializovat pod jinou verzi. Konkrétně některé seřazené kolekce (jako je <xref:System.Collections.Hashtable?displayProperty=name>) tak, aby objekty z těchto typů nelze deserializovat pomocí rozhraní .NET 4.0, pokud byly serializovat s příznakem .NET 4.5 přidat členy mezi 4.0 a 4.5. Všimněte si, že pokud serializovaná data jak serializovat a deserializovat se stejnou verzí rozhraní .NET Framework, žádné problému.|
|Návrh|<xref:System.Runtime.Serialization.Formatters.Soap.SoapFormatter?displayProperty=name> měl by být nahrazen serializace <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter?displayProperty=name> serializace nebo <xref:System.Runtime.Serialization.NetDataContractSerializer?displayProperty=name> chcete být odolní vůči změny rozhraní .NET Framework.|
|Rozsah|Vedlejší|
|Version|4.5|
|Typ|Modul runtime|
|Ovlivněné rozhraní API|<ul><li><xref:System.Runtime.Serialization.Formatters.Soap.SoapFormatter.Serialize(System.IO.Stream,System.Object)?displayProperty=nameWithType></li><li><xref:System.Runtime.Serialization.Formatters.Soap.SoapFormatter.Serialize(System.IO.Stream,System.Object,System.Runtime.Remoting.Messaging.Header[])?displayProperty=nameWithType></li><li><xref:System.Runtime.Serialization.Formatters.Soap.SoapFormatter.Deserialize(System.IO.Stream)?displayProperty=nameWithType></li><li><xref:System.Runtime.Serialization.Formatters.Soap.SoapFormatter.Deserialize(System.IO.Stream,System.Runtime.Remoting.Messaging.HeaderHandler)?displayProperty=nameWithType></li></ul>|


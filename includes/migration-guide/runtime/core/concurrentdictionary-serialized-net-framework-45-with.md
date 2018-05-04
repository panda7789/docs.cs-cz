### <a name="a-concurrentdictionary-serialized-in-net-framework-45-with-netdatacontractserializer-cannot-be-deserialized-by-net-framework-451-or-452"></a>ConcurrentDictionary serializována v rozhraní .NET Framework 4.5 s NetDataContractSerializer nelze deserializovat pomocí rozhraní .NET Framework 4.5.1 nebo 4.5.2

|   |   |
|---|---|
|Podrobnosti|Z důvodu vnitřní změn na typ <xref:System.Collections.Concurrent.ConcurrentDictionary%602> objekty, které se serializují pomocí rozhraní .NET Framework 4.5 pomocí <xref:System.Runtime.Serialization.NetDataContractSerializer?displayProperty=name> nelze deserializovat v rozhraní .NET Framework 4.5.1 nebo v rozhraní .NET Framework 4.5.2.Note v jiných směr (který přesunutí serializace s rozhraním .NET Framework 4.5.x a deserializace pomocí rozhraní .NET Framework 4.5) funguje. Podobně všechny serializace mezi různými verzemi 4.x pracuje s 4.6.Serializing rozhraní .NET Framework a deserializaci z jedné verze rozhraní .NET Framework nejsou dotčena.|
|Návrh|Pokud je nutné k serializaci a deserializaci <xref:System.Collections.Concurrent.ConcurrentDictionary%602?displayProperty=name> mezi rozhraní .NET Framework 4.5 a 4.5.1/4.5.2 rozhraní .NET Framework, jako například serializátor alternativní <xref:System.Runtime.Serialization.DataContractSerializer?displayProperty=name> nebo <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter?displayProperty=name> serializátor by měl použít místo <xref:System.Runtime.Serialization.NetDataContractSerializer?displayProperty=name>. Případně protože je tento problém řešit v rozhraní .NET Framework 4.6, se může být vyřešen upgrade na tuto verzi rozhraní .NET Framework.|
|Rozsah|Vedlejší|
|Version|4.5.1|
|Typ|Modul runtime|


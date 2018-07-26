### <a name="netdatacontractserializer-fails-to-deserialize-a-concurrentdictionary-serialized-with-a-different-net-version"></a>NetDataContractSerializer se nepodařilo deserializovat ConcurrentDictionary serializovat s příznakem jinou verzi rozhraní .NET

|   |   |
|---|---|
|Podrobnosti|Standardně <xref:System.Runtime.Serialization.NetDataContractSerializer?displayProperty=name> lze použít pouze v případě, že i serializaci a deserializaci končí sdílet stejné typy CLR. Proto není zaručeno, že objekt serializovat s příznakem jednu verzi rozhraní .NET Framework lze deserializovat jinou verzí.<xref:System.Collections.Concurrent.ConcurrentDictionary%602?displayProperty=name> je typ, který je známý nechcete správně deserializovat, je-li serializovat pomocí rozhraní .NET Framework 4.5 nebo dřívější a deserializovat s použitím rozhraní .NET Framework 4.5.1 nebo novější.|
|Návrh|Existuje několik možných řešeních tohoto problému:<ul><li>Upgrade serializaci počítač k používání rozhraní .NET Framework 4.5.1, také.</li><li>Použití <xref:System.Runtime.Serialization.DataContractSerializer?displayProperty=name> místo <xref:System.Runtime.Serialization.NetDataContractSerializer?displayProperty=name> jako to neočekává přesně stejné typy CLR serializaci a deserializaci skončí.</li><li>Použití <xref:System.Collections.Generic.Dictionary%602?displayProperty=name> místo <xref:System.Collections.Concurrent.ConcurrentDictionary%602?displayProperty=name> od neproběhne této konkrétní 4.5 –&gt;4.5.1 přerušit.</li></ul>|
|Rozsah|Vedlejší|
|Version|4.5.1|
|Typ|Modul runtime|
|Ovlivněné rozhraní API|<ul><li><xref:System.Runtime.Serialization.NetDataContractSerializer.Deserialize(System.IO.Stream)?displayProperty=nameWithType></li></ul>|


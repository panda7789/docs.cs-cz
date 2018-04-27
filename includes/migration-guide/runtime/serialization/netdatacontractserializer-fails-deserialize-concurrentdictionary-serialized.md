### <a name="netdatacontractserializer-fails-to-deserialize-a-concurrentdictionary-serialized-with-a-different-net-version"></a>NetDataContractSerializer nepodaří deserializovat ConcurrentDictionary serializovat s jinou verzi rozhraní .NET

|   |   |
|---|---|
|Podrobnosti|Standardně <xref:System.Runtime.Serialization.NetDataContractSerializer?displayProperty=name> lze použít pouze v případě, že jak serializaci a deserializaci končí sdílet stejné typy CLR. Proto není zaručeno, že z jiné verze lze deserializovat objekt serializovat s příznakem jednu verzi rozhraní .NET Framework. <xref:System.Collections.Concurrent.ConcurrentDictionary%602?displayProperty=name> je typ, který je známý k není k deserializaci správně, pokud serializovat v rozhraní .NET Framework 4.5 nebo starším a deserializovat s rozhraním .NET Framework 4.5.1 nebo novější.|
|Návrh|Existuje několik možných řešeních tohoto problému:<ul><li>Upgrade serializaci počítač k používání rozhraní .NET Framework 4.5.1, také.</li><li>Použití <xref:System.Runtime.Serialization.DataContractSerializer?displayProperty=name> místo <xref:System.Runtime.Serialization.NetDataContractSerializer?displayProperty=name> jako neočekává přesný stejné typy CLR v jak serializaci a deserializaci elementy end.</li><li>Použití <xref:System.Collections.Generic.Dictionary%602?displayProperty=name> místo <xref:System.Collections.Concurrent.ConcurrentDictionary%602?displayProperty=name> vzhledem k tomu, že neproběhne této konkrétní 4.5 -&gt;rozdělit 4.5.1.</li></ul>|
|Rozsah|Vedlejší|
|Version|4.5.1|
|Typ|Modul runtime|
|Ovlivněné rozhraní API|<ul><li><xref:System.Runtime.Serialization.NetDataContractSerializer.Deserialize(System.IO.Stream)?displayProperty=nameWithType></li></ul>|


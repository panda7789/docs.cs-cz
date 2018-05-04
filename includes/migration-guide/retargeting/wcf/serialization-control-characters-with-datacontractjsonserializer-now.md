### <a name="serialization-of-control-characters-with-datacontractjsonserializer-is-now-compatible-with-ecmascript-v6-and-v8"></a>Serializace řídicí znaky s DataContractJsonSerializer je teď kompatibilní s ECMAScript V6 a v8:

|   |   |
|---|---|
|Podrobnosti|V rozhraní .NET framework 4.6.2 a dřívějších verzích <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer?displayProperty=name> není serializovat některé speciální řídicí znaky, jako je například \b \f a \t tak, aby byla kompatibilní se standardy ECMAScript V6 a v8:. Od verze 4.7 rozhraní .NET Framework, je kompatibilní s ECMAScript V6 a v8: serializace tyto řídicí znaky.|
|Návrh|Pro aplikace, které cílí rozhraní .NET Framework 4.7 je tato funkce povolená ve výchozím nastavení. Pokud toto chování není žádoucí, můžete zamítnutí této funkce přidáním následující řádek do <code>&lt;runtime&gt;</code> v souboru app.config nebo web.config:<pre><code class="lang-xml">&lt;runtime&gt;&#13;&#10;&lt;AppContextSwitchOverrides value=&quot;Switch.System.Runtime.Serialization.DoNotUseECMAScriptV6EscapeControlCharacter=false&quot; /&gt;&#13;&#10;&lt;/runtime&gt;&#13;&#10;</code></pre>|
|Rozsah|Edge|
|Version|4.7|
|Typ|Změna orientace|
|Ovlivněné rozhraní API|<ul><li><xref:System.Runtime.Serialization.Json.DataContractJsonSerializer.WriteObject(System.IO.Stream,System.Object)?displayProperty=nameWithType></li><li><xref:System.Runtime.Serialization.Json.DataContractJsonSerializer.WriteObject(System.Xml.XmlDictionaryWriter,System.Object)?displayProperty=nameWithType></li><li><xref:System.Runtime.Serialization.Json.DataContractJsonSerializer.WriteObject(System.Xml.XmlWriter,System.Object)?displayProperty=nameWithType></li></ul>|

